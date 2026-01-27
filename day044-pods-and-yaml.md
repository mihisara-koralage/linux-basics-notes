# Day 44 – Pods & YAML
## YAML structure
A Kubernetes YAML file is:
- A declaration of what you want
- Not a script
- Not step-by-step commands
```yaml
apiVersion:
kind:
metadata:
spec:
```
## Pod example
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80

```
## Explanation of each field
- apiVersion
  - Which version of Kubernetes API
  - Example: ```v1```

- kind
  - Type of object
  - Here: Pod

- metadata
  - Identifies the object
  - Name, labels, etc.

- spec
  - Desired state
  - What containers to run
  - Images, ports, volumes
## Declarative mindset notes
### Imperative (Docker-style):
```bash
docker run nginx
```
### Declarative (Kubernetes-style):
```bash
image: nginx
replicas: 3
```
## How Kubernetes Uses YAML
```arduino
YAML file
   |
kubectl apply
   |
API Server
   |
Scheduler
   |
Node
   |
Pod running
```
