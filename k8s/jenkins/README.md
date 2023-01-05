# Jenkins k8s Deployment

This Jenkins k8s deployment uses the [Jenkins image](https://github.com/acschm1d/cloud-collections/tree/main/images/jenkins) from this repository.

## Volume and Security

This configuration uses the local node storage which is **insufficient for production systems**. For use cases other then testing or development environments consider another [storage class provisioner](https://kubernetes.io/docs/concepts/storage/storage-classes/#provisioner).

By default, credentials for Jenkins are set to `admin` as user and `admin` as password. Change that accordingly.

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
NAME                       READY   STATUS    RESTARTS   AGE
jenkins-68675bf956-9qrl5   1/1     Running   0          5s
```

Tunnel the service to make it accesible to the host:

```
minikube tunnel jenkins --url
```

Login at the printed URL with your defined credentials.
