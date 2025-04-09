# PART 1: `nodeSelector` – Target a specific worker

## Step 1. Label the node


```
kubectl label node kind-worker disktype=ssd
```

Verify:

```
kubectl get nodes --show-labels
```

You should see `disktype=ssd` next to `kind-worker`.

# PART 2: Taints & Tolerations – Prevent Pod scheduling on a node

## Step 1. Taint the node

```
kubectl taint nodes kind-worker2 dedicated=testing:NoSchedule
```

Check:

```
kubectl describe node kind-worker2 | grep Taint
```

# PART 3: Affinity – Schedule Pods near other Pods
