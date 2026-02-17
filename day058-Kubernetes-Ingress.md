# Day 58 — Kubernetes Ingress
## What is Ingress
- Smart routing layer for Kubernetes
- Routes traffic using domains or paths
- Avoids many NodePorts/LoadBalancers

## Ingress Controller vs Ingress Resource
- Controller = traffic engine
- Resource = routing rules

## Why Ingress is Useful
- One entry point
- Domain-based routing
- Production-ready setup

## Example Ingress YAML
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
  - host: myapp.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: nginx-service
            port:
              number: 80
```
### Hosts File Trick
```
127.0.0.1 myapp.local
```
Maps domain to localhost.
