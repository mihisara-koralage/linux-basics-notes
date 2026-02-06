# Day 52 — Kubernetes Logs & Monitoring
Learned how to:
## View pod logs using kubectl logs
```bash
kubectl logs <pod-name>
```
## Stream live logs with -f
```bash
kubectl logs -f <pod-name>
```
## Inspect pods using kubectl describe
```bash
kubectl describe pod <pod-name>
```
## Monitor resource usage using kubectl top
```
kubectl top pods
```
## Understand observability basics (logs vs metrics)
Logs:
- Records of events
- Example: nginx access logs

Metrics:
- Numbers over time
- Example:
  - CPU %
  - Memory usage
- Practiced debugging nginx pods.
