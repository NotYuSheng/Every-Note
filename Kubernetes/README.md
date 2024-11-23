# Kubernetes-Cheatsheet
## Starts a Minikube cluster
```
minikube start
```

### Specify with driver (eg. docker, kvm2, virtualbox, ssh, ...)
```
minikube start --driver=docker
```

## Stop the cluster
```
minikube stop
```

## Delete the cluster
```
minikube delete
```

## Check cluster status
```
minikube status
```

## List available nodes
```
kubectl get nodes
```

## Check the Pod events
```
kubectl describe pod <pod-name>
```

## View Pod logs
```
kubectl logs <pod-name>
```

## Access Kubernetes Dashboard
```
minikube dashboard
```

## Access a service
```
minikube service <service-name>
```