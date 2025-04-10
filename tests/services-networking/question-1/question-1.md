## Show the Service:
```
kubectl get svc my-service
```
## Show the Deployment:
```
kubectl get deployment nginx-deployment
```
## Show the Pods (created by the Deployment):
```
kubectl get pods -l app=nginx
```
## Show the ReplicaSet behind the Deployment:
```
kubectl get rs
```
## Show the Endpoints (what your Service connects to):
```
kubectl get endpoints my-service
```

## On the CKA exam environment, when you expose a Service using NodePort, you can typically access it with:

```
curl localhost:<NodePort>
```
