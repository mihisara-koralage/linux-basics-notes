# Day 075 – Rolling Updates in Kubernetes

## 🎯 Objective

Deploy new application versions without downtime.

---

## 🧠 Rolling Update

Kubernetes gradually replaces old pods with new pods.

Ensures application remains available.

---

## 🛠 Practical

Created deployment:

kubectl create deployment rolling-demo --image=nginx:1.23 --replicas=3

Updated image:

kubectl set image deployment/rolling-demo nginx=nginx:1.25

Watched rollout:

kubectl get pods -w

---

## 🔄 Rollout Commands

Check status:

kubectl rollout status deployment/rolling-demo

Check history:

kubectl rollout history deployment/rolling-demo

---

## 🧠 Key Takeaway

Rolling updates allow zero downtime deployments in Kubernetes.
