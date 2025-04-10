# 🧪 CKA Practice Playground 🧠

Welcome to my **Certified Kubernetes Administrator (CKA)** practice repo!  
This is where I break things *on purpose* so I can fix them like a pro 💪

---

## 🛠️ What's This Repo About?

This is **not** a polished production setup.  
This is **pure terminal kung fu**, where:

- Every YAML is handcrafted with 💚 in **vim**
- All commands are typed (and mistyped) in **kubectl**
- Everything runs in lightweight, ephemeral **kind** clusters (Kubernetes in Docker)

Think of this as my digital dojo where I sharpen my Kubernetes-fu, one `kubectl get pods` at a time.

---

## 🔁 Workflow

1. `kind create cluster`
2. `vim my-deployment.yaml`
3. `kubectl apply -f my-deployment.yaml`
4. Debug when things go wrong (and they *will*)
5. Repeat until enlightenment ✨

---

## 📂 What's Inside?

- 🧾 Sample manifests (Deployments, Services, Ingress, etc.)
- 🔧 Troubleshooting scenarios
- ⚙️ RBAC configs
- 🗃️ Etcd backups/restores
- 🔄 Upgrades, node management, and more...

Everything is written, edited, and managed **directly in the terminal**. No fancy UIs, no shortcuts.

---

## 📚 Why?

Because CKA doesn't care about your IDE.  
It cares if you can **solve real-world Kubernetes problems quickly and confidently** in a CLI-only environment.

