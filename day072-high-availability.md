# Day 072 – High Availability in Kubernetes

## 🎯 Objective
Understand how Kubernetes ensures application availability using replicas.

---

## 🧠 What is High Availability?

System continues operating even when components fail.

Kubernetes provides HA using replicas.

---

## 🛠 Practical Done

Created deployment with 3 replicas:

kubectl create deployment ha-demo --image=nginx --replicas=3

Verified pods:

kubectl get pods -l app=ha-demo

Deleted one pod to simulate failure:

kubectl delete pod <pod-name>

Observed Kubernetes automatically recreated pod.

---

## 🔄 Self-Healing Behavior

- Deployment maintains desired replica count
- Controller detects pod failure
- New pod created automatically

---

## 🧠 High Availability vs Disaster Recovery

High Availability → prevent downtime  
Disaster Recovery → recover after failure

---

## 🚨 Key Takeaway

Multiple replicas enable Kubernetes self-healing and prevent downtime.
