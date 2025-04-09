# Kubernetes Cluster Maintenance - AWS Analogy

This guide explains essential cluster maintenance operations in Kubernetes and maps them to AWS equivalents for easier real-world understanding.

---

## Topics Covered

| K8s Topic            | Purpose                                      |
|----------------------|----------------------------------------------|
| `cordon` / `drain`   | Safely remove a node from scheduling         |
| Upgrade strategy     | Control version upgrades (via kubeadm)      |
| ETCD backup/restore  | Save and restore the cluster's state        |

---

## 1. Node Cordon / Drain

### Cordon a Node
Prevents **new Pods** from being scheduled on a node:
```bash
kubectl cordon <node-name>
```

### Drain a Node
Evicts **all running Pods**, except DaemonSets:
```bash
kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data
```

To bring it back:
```bash
kubectl uncordon <node-name>
```

### 🔄 AWS Analogy
| K8s Action         | AWS Equivalent                                   |
|--------------------|--------------------------------------------------|
| `cordon`           | Remove EC2 from ELB target group                 |
| `drain`            | Put EC2 in ASG standby / rolling update step     |

---

## 2. Cluster Upgrade (via kubeadm)

These are the steps you'd run on a control-plane node:

### Plan the Upgrade
```bash
kubeadm upgrade plan
```

### Apply the Upgrade
```bash
kubeadm upgrade apply v1.xx.x
```

### Upgrade Worker Nodes
```bash
kubectl drain <worker-node> --ignore-daemonsets
kubeadm upgrade node
kubectl uncordon <worker-node>
```

### 🔄 AWS Analogy
| K8s Upgrade Step     | AWS Equivalent                            |
|----------------------|---------------------------------------------|
| `kubeadm upgrade`    | Replace EC2 AMI in ASG / Rolling replacement |
| `drain` before upgrade | Detach instance from ELB temporarily      |

---

## 3. ETCD Backup & Restore

### Backup ETCD
```bash
ETCDCTL_API=3 etcdctl snapshot save /backup/etcd-snapshot.db \
--endpoints=https://127.0.0.1:2379 \
--cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/server.crt \
--key=/etc/kubernetes/pki/etcd/server.key
```

### Restore ETCD
```bash
ETCDCTL_API=3 etcdctl snapshot restore /backup/etcd-snapshot.db \
--data-dir=/var/lib/etcd-from-backup
```

Then reconfigure the static pod manifest (`/etc/kubernetes/manifests/etcd.yaml`) to point to the new data dir.

### 🔄 AWS Analogy
| K8s ETCD Task         | AWS Equivalent                            |
|------------------------|--------------------------------------------|
| `etcdctl snapshot save`| RDS / DynamoDB snapshot                    |
| `etcdctl restore`      | Restore RDS backup or DB failover          |

---

## Summary Table

| Kubernetes Task          | AWS Analogy                                      |
|---------------------------|--------------------------------------------------|
| Cordon a node             | Remove EC2 from ELB or place in standby          |
| Drain a node              | Instance replacement or pre-maintenance step     |
| kubeadm upgrade           | Rolling update / launch template replacement     |
| etcd backup / restore     | RDS snapshot & restore, or backup/restore DB     |

---

## Final Notes
- These tasks often require SSH access or `sudo`
- They affect **cluster stability** and should be tested in non-prod
- CKA exam will expect you to do these **quickly but safely**

Use this guide to map what you already know from AWS into how Kubernetes operates in production environments.
