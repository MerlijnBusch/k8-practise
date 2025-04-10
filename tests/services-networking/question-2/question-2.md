## One-Liner: Curl a LoadBalancer Service (CKA)

```
NODE_IP=$(kubectl get nodes -o jsonpath='{.items[0].status.addresses[?(@.type=="InternalIP")].address}')
NODE_PORT=$(kubectl get svc my-service -o jsonpath='{.spec.ports[0].nodePort}')
curl http://$NODE_IP:$NODE_PORT
```

## Show all elements
```
kubectl get deployments
kubectl get pods -o wide
kubectl get services
kubectl get endpoints
```
