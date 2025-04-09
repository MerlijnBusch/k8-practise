## Apply all:

```
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pod-with-pvc.yaml
```

Check:

```
kubectl get pv,pvc
```

If it says `Bound` — success!




| AWS Concept                     | Kubernetes Equivalent                         |
|--------------------------------|-----------------------------------------------|
| EBS volume                     | PersistentVolume (PV)                         |
| Attach EBS to instance         | PersistentVolumeClaim bound to a Pod          |
| Mount volume inside instance   | volumeMount inside the Pod’s container        |
| Instance Store (ephemeral)     | emptyDir volume (non-persistent)              |
| Filesystem path (e.g. /mnt/data) | mountPath in container                      |

