```
kubectl -n ns-nginx rollout history deployment nginx-deploy
kubectl -n ns-nginx rollout undo deployment nginx-deploy
deployment.apps/nginx-deploy rolled back

kubectl -n ns-nginx get replicaset
NAME                      DESIRED   CURRENT   READY   AGE
nginx-deploy-55679458fd   0         0         0       3m37s
nginx-deploy-5c8bfcc47c   5         5         5       5m44s

kubectl -n ns-nginx get pods -o wide
NAME                            READY   STATUS    RESTARTS   AGE   IP            NODE         NOMINATED NODE   READINESS GATES
nginx-deploy-5c8bfcc47c-8kfck   1/1     Running   0          43s   10.244.2.11   k8s-node-2   <none>           <none>
nginx-deploy-5c8bfcc47c-hqlxd   1/1     Running   0          44s   10.244.1.12   k8s-node-1   <none>           <none>
nginx-deploy-5c8bfcc47c-rb8gn   1/1     Running   0          44s   10.244.2.10   k8s-node-2   <none>           <none>
nginx-deploy-5c8bfcc47c-tjbcw   1/1     Running   0          43s   10.244.1.13   k8s-node-1   <none>           <none>
nginx-deploy-5c8bfcc47c-vvdfr   1/1     Running   0          44s   10.244.1.11   k8s-node-1   <none>           <none>

kubectl -n ns-nginx get pods nginx-deploy-57767fb8cf-zklv4 -o jsonpath='{.spec.containers[0].image}'
nginx:1.22
```


