# Day 55 – Kubernetes Networking

## Key Learnings

### Kubernetes Services
Services provide stable access to pods.

Traffic flow:
User → Service → Pod

Pods are temporary, but Services provide a fixed endpoint.

---

## Types of Services

### 1. ClusterIP
- Default type
- Internal communication only
- Used for microservices

### 2. NodePort
- Exposes app via NodeIP:Port
- Used for local testing
- Example: http://localhost:30007

### 3. LoadBalancer
- Provides external IP
- Used in cloud production
- Works with AWS/GCP/Azure

---

## Commands Used
```bash
kubectl get svc
```
