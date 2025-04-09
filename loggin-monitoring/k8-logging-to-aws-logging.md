# Kubernetes Logging & Monitoring - AWS Analogy

## Mapping K8s Probes, Logs, and Events to AWS

| Kubernetes Concept       | AWS Equivalent                                |
|--------------------------|-----------------------------------------------|
| `livenessProbe`          | EC2 health check / ELB instance restart       |
| `readinessProbe`         | ELB target group health check                 |
| `kubectl logs`           | EC2 logs, CloudWatch logs                     |
| `kubectl get events`     | CloudTrail events, CloudWatch alerts          |

---

## 1. Probes = AWS Health Checks

| Kubernetes Probe      | AWS Equivalent                              |
|------------------------|---------------------------------------------|
| `livenessProbe`       | EC2 or ELB health check → restart container |
| `readinessProbe`      | ELB Target Group Health Check               |

- `livenessProbe`: Is the app alive? If not → **restart container**
- `readinessProbe`: Is the app ready to receive traffic? If not → **don’t send traffic**

---

## 2. Logs = CloudWatch Logs or EC2 System Logs

| K8s Command              | AWS Equivalent                    |
|--------------------------|------------------------------------|
| `kubectl logs <pod>`     | EC2 logs or `tail /var/log/*.log`  |
| `kubectl logs -f <pod>`  | CloudWatch Logs streaming         |

These are raw container logs. In production, you would forward them to tools like:
- CloudWatch
- Fluentd / Promtail
- ELK Stack

---

## 3. Events = CloudTrail or CloudWatch Events

Kubernetes Events explain what’s happening at the control plane level:
- Pod failed to schedule
- Image pull errors
- Node conditions, etc.

Run:
```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

Equivalent AWS services:
- **CloudTrail** (control plane auditing)
- **CloudWatch Events / Alarms** (cluster-level alerts)

---

## Summary Table

| Kubernetes              | AWS Equivalent                             |
|-------------------------|--------------------------------------------|
| `livenessProbe`         | EC2/ELB health check                       |
| `readinessProbe`        | ELB target readiness check                |
| `kubectl logs`          | EC2 logs / CloudWatch Logs                |
| `kubectl get events`    | CloudTrail events, CloudWatch monitoring  |
| Log forwarding (Fluentd)| CloudWatch Agent / Lambda log shipping    |

---

Use this mapping to understand how Kubernetes handles health checking, observability, and system behavior — with direct comparisons to familiar AWS tools.
