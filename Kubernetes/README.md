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

## Get shell in pod
kubectl exec -it <pod-name> -- <command>

## Check cluster status
```
minikube status
```

## List available nodes in namespace
```
kubectl get nodes -n <namespace>
```

## Check the Pod events
```
kubectl describe pod <pod-name>
```

## View Pod logs
```
kubectl logs <pod-name>
```

## Permanently stop and delete the Pods
```
kubectl delete deployment --all --all-namespaces
```

## Delete all pods in specific namespace
```
kubectl delete namespace <namespace-name>
```

## Access Kubernetes Dashboard
```
minikube dashboard
```

## Access a service
```
minikube service <service-name>
```
