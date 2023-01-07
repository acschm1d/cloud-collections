# nginx k8s Deployment

Basic example of deploying nginx webserver with ingress routing.

## Spin up a cluster

For local development you can start with lightweigtht tools such as [minikube](https://minikube.sigs.k8s.io/docs/start/). To route traffic to the ingress controller, the ingress addon for minikube needs to be enabled as well.

```
minikube start
minikube addons enable ingress
```

## Build

Once your cluster is ready apply the configuration file:

```
kubectl apply -f deployment.yaml
```

Verify that the pods are running:

```
kubectl get pods
NAME                              READY   STATUS    RESTARTS   AGE
web-deployment-549c88d4c7-g8j55   1/1     Running   0          5s
web-deployment-549c88d4c7-stmmd   1/1     Running   0          5s
```

Tunnel the traffic to the ingress controller:

```
minikube tunnel
```

The nginx webserver is now available at `http://localhost`.
