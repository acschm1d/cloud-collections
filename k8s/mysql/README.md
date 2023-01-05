# MySQL k8s Deployment

## Volume and Security

This configuration uses the local node storage which is **insufficient for production systems**. For use cases other then testing or development environments consider another [storage class provisioner](https://kubernetes.io/docs/concepts/storage/storage-classes/#provisioner).

`root` user is used to access the database which is not secure. It goes without saying that for productive use it is recommended to secure the `root` user and create dedicated database users with limited privileges.

## Spin up a cluster

For local development you can start with lightweigtht tools such as [minikube](https://minikube.sigs.k8s.io/docs/start/).

```
minikube start
```

## Build

Once your cluster is ready apply the configuration files:

```
kubectl apply -f .
```

Verify that the pod is running:

```
kubectl get pods
NAME      READY   STATUS        RESTARTS      AGE
mysql-0   1/1     Running       0             5s
```

Operate the database by accessing the pod:

```
kubectl exec -it mysql-0 -- bash
mysql -u root -p
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)
```
