# Day 56 – Kubernetes Health Probes

Today I learned about Kubernetes health probes.

## Liveness Probe
- Checks if container is alive
- Restarts container if it fails
- Prevents stuck applications

Example:
```yaml
livenessProbe:
  httpGet:
    path: /
    port: 80
  initialDelaySeconds: 10
  periodSeconds: 5
```
## Readiness Probe
- Checks if pod is ready to receive traffic
- If failed, traffic is stopped to the pod
- Does NOT restart container

## Why Probes Matter
- Improve reliability
- Auto-recovery from failures
- Used in real production systems
