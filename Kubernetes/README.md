# Kubernetes-Cheatsheet
## Cluster
### Starts a Minikube cluster
```
minikube start
```

#### Specify with driver (eg. docker, kvm2, virtualbox, ssh, ...)
```
minikube start --driver=docker
```

### Stop the cluster
```
minikube stop
```

### Delete the cluster
```
minikube delete
```

## Pod
### List pods
```
kubectl get pods
```

### Create pod described using yaml
```
kubectl run <pod-name> --image=<image-name> --restart=Never --dry-run=client -n <namespace> -o yaml > <pod-filename.yaml>
```

## Stop pod
```
kubectl delete pod <pod-name>
```

### Get shell in pod
```
kubectl exec -it <pod-name> -- <command>
```

## General
### Check cluster status
```
minikube status
```

### List available nodes in namespace
```
kubectl get nodes -n <namespace>
```

### Check the Pod events
```
kubectl describe pod <pod-name>
```

### View Pod logs
```
kubectl logs <pod-name>
```

### Permanently stop and delete the Pods
```
kubectl delete deployment --all --all-namespaces
```

### Delete all pods in specific namespace
```
kubectl delete namespace <namespace-name>
```

### Access Kubernetes Dashboard
```
minikube dashboard
```

### Access a service
```
minikube service <service-name>
```

## Custom Config
Set nano as persistent default kubectl edit editor
```
echo 'export KUBE_EDITOR=nano' >> ~/.bashrc
source ~/.bashrc
```
