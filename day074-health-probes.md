# Day 074 – Liveness vs Readiness Probes

## 🎯 Objective

Understand Kubernetes health checks for container reliability.

---

## 🧠 Problem

Container running does not mean application is healthy.

Kubernetes needs health checks.

---

## 🔍 Liveness Probe

- Checks if container is alive
- If failed → container restarted
- Provides self-healing

---

## 🚦 Readiness Probe

- Checks if app ready for traffic
- If failed → no traffic sent
- Prevents user errors

---

## 🛠 Practical

Created deployment with:

- livenessProbe
- readinessProbe

Used HTTP check on `/`

Applied:

kubectl apply -f health-probe.yaml

Verified using:

kubectl describe pod

---

## 🧠 Key Difference

Liveness → restart container  
Readiness → stop traffic

---

## 🚨 Key Takeaway

Health probes enable Kubernetes to automatically detect and recover unhealthy containers.
