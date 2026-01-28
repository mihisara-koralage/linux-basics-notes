# Day 45 – Deployments & Scaling
## Why Pods aren’t enough
Pods are:
- Not self-healing by themselves
- Not scalable easily
- Not good for updates

If a Pod dies → it stays dead (unless something manages it).
## Deployment concept
A Deployment is:
- A higher-level Kubernetes object
- Manages Pods for you
- Ensures the desired number of replicas is always running
## ReplicaSet relationship
```text
Deployment
   |
ReplicaSet
   |
Pods -> Container
```
- Deployment: what you define
- ReplicaSet: ensures correct number of Pods
- Pods: run containers

## Scaling & rolling updates
To scale:
- Change replicas: 3 → 5
- Apply YAML again
- Kubernetes creates new Pods automatically

Rolling updates:
When you update image version:
- Old Pods are replaced gradually
- New Pods start before old ones stop
- Users don’t notice
## Simple Deployment YAML
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```
replicas:
- Number of Pods to run
- Change this → auto scale

selector:
- How Deployment finds its Pods

template: 
- Pod definition inside Deployment
- Same structure as Pod YAML
