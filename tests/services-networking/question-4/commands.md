# Basic command to "sh" into a pod:

```
kubectl exec -it <pod-name> -- sh
```

    `-i` = interactive

    `-t` = allocate a pseudo-terminal

    `--` separates kubectl options from the command you want to run inside the container
