## TL;DR: Commands to Remember

```
# Probes
kubectl describe pod <pod-name>         # See probe results

# Logs
kubectl logs <pod-name>                 # View container output
kubectl logs -f <pod-name>              # Stream logs

# Events
kubectl get events --sort-by=.metadata.creationTimestamp
```
