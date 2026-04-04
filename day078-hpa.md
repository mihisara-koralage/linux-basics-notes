# Day 078 – Horizontal Pod Autoscaler (HPA)

## 🎯 Objective

Automatically scale pods based on CPU usage.

---

## 🧠 Problem

Traffic increases overload pods.

Manual scaling not efficient.

---

## 🚀 HPA

Horizontal Pod Autoscaler scales pods automatically.

Based on CPU usage.

---

## 🛠 Practical

Created deployment:

kubectl create deployment hpa-demo --image=nginx --replicas=2

Created HPA:

kubectl autoscale deployment hpa-demo \
  --cpu-percent=50 \
  --min=2 \
  --max=5

Checked:

kubectl get hpa

---

## 🧪 Load Testing

Used busybox to generate traffic.

Observed replicas increase automatically.

---

## 🧠 Key Takeaway

HPA enables automatic scaling based on load.
