# Day 46 – Kubernetes Services
## Why Services are needed
- Provides a stable IP & DNS name
- Routes traffic to Pods
- Uses labels/selectors to find Pods
## Service → Pod relationship
```text
User
 |
 v
Service (stable IP)
 |
 v
Pods (dynamic IPs)
```
## Service types
### ClusterIP (Default)
- Internal access only
- Used for backend services
```text
App A --> Service --> App B
```
### NodePort
- Exposes service on each node’s IP
- Used for testing / learning
```text
NodeIP:30080 --> Service --> Pods
```
### LoadBalancer
- Used in cloud (AWS, GCP, Azure)
- Creates external load balancer
- Production-ready
```text
Internet --> LoadBalancer --> Service --> Pods
```
## Simple Service YAML
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
```
