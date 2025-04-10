```
# Run the pod:
kubectl apply -f pod.yaml

# Check the env variable:
kubectl exec busybox -- env | grep PLANET
PLANET=blue
```
