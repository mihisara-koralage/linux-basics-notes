# Day 077 – Resource Requests & Limits

## 🎯 Objective

Control CPU and memory usage for containers.

---

## 🧠 Problem

Pods may consume all node resources.

Causes performance issues.

---

## 🧠 Requests vs Limits

Requests → minimum guaranteed resources  
Limits → maximum allowed resources

---

## 🛠 Practical

Created deployment with resources:

requests:
  cpu: 100m
  memory: 64Mi

limits:
  cpu: 200m
  memory: 128Mi

Applied:

kubectl apply -f resource-demo.yaml

Verified using:

kubectl describe pod

---

## 🧠 Key Takeaway

Resource limits prevent noisy neighbor problems and stabilize cluster performance.
