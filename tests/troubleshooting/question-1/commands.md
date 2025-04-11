```
kubectl get pods -n kube-system

# API Server logs
kubectl -n kube-system logs kube-apiserver-kind-control-plane

# Controller Manager logs
kubectl -n kube-system logs kube-controller-manager-kind-control-plane

# Scheduler logs
kubectl -n kube-system logs kube-scheduler-kind-control-plane
```
