# Day 50 – Ingress
## NodePort vs LoadBalancer vs Ingress
### NodePort
- Opens random ports
- Hard to manage
- Not production friendly

### LoadBalancer
- Each service gets its own IP
- Expensive in cloud
- Not scalable for many apps

### An Ingress:
- Routes external traffic to services
- Works with domains (URLs)
- Acts like a smart router
## Ingress concept
```nginx
Internet
   |
Ingress
   |
Services
   |
Pods
```
### Example Routing
```bash
myapp.com      → App1
api.myapp.com  → App2
myapp.com/blog → App3
```
## Controller role
Ingress alone does nothing.

You need an:

Ingress Controller

Common ones:
- NGINX Ingress Controller
- Traefik
- HAProxy

Controller actually handles traffic.
## Example YAML
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
  - host: myapp.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: my-service
            port:
              number: 80
```
