# Day 57 – Kubernetes Autoscaling (HPA)

## What is HPA?
Horizontal Pod Autoscaler automatically scales pods based on CPU or memory usage.

## Why HPA?
- Handles high traffic
- Saves cost
- Improves availability

## Example Command
```bash
kubectl autoscale deployment nginx-demo --cpu-percent=50 --min=2 --max=10
```
## Key Learning
Kubernetes can scale applications automatically depending on load.
