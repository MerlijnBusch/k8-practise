Create secret.

```
echo -n 'admin' > username
echo -n 'admin-pass' > password

kubectl create secret generic admin-cred --from-file=username --from-file=password
```

```
kubectl apply -f secretenv.yaml

kubectl exec secretenv -- env | grep -E "USERNAME|PASSWORD"
USERNAME=admin
PASSWORD=admin-pass
```

```
kubectl apply -f secretvolume.yaml

kubectl exec secretvolume -- ls /etc/admin-cred
password
username

kubectl exec secretvolume -- cat /etc/admin-cred/username
admin

kubectl exec secretvolume -- cat /etc/admin-cred/password
admin-pass
```
