# Day 067 – etcd Fundamentals

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![etcd](https://img.shields.io/badge/etcd-Distributed-419EDA?style=for-the-badge&logo=etcd&logoColor=white)
![Key-Value](https://img.shields.io/badge/Key--Value-Store-4CAF50?style=for-the-badge&logoColor=white)

---

## 🎯 Objective
Understand how Kubernetes stores cluster state using etcd.

---

## 🧠 What is etcd?

- Distributed key-value store
- Stores entire cluster state
- Acts as Kubernetes brain

Architecture flow:
kubectl → kube-apiserver → etcd

---

## 🏗 What etcd Stores

- Pods
- Deployments
- Services
- Secrets
- ConfigMaps
- Nodes
- RBAC rules

---

## 🧪 Practical Done Today

1. Created namespace `etcd-test`
2. Deployed nginx
3. Verified deployment exists
4. Deleted deployment
5. Observed state change

---

## 💥 What Happens If etcd Fails?

- API server cannot function
- Controllers stop
- Scheduler stops
- Cluster becomes unusable

---

## 🧠 Key Takeaways

- etcd stores desired state
- Kubernetes is state-driven
- etcd backup is critical in self-managed clusters
- Managed cloud clusters handle etcd automatically

---

## 💬 Interview Question I Can Answer

What happens if etcd fails in Kubernetes?