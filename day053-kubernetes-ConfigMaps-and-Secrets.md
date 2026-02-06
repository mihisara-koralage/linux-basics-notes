# Day 53: ConfigMaps & Secrets in Kubernetes
##  Create a ConfigMap
```bash
kubectl create configmap app-config --from-literal=APP_COLOR=blue
```
### Verify
```bash
kubectl get configmaps
kubectl describe configmap app-config
```
## Create a Secret
```bash
kubectl create secret generic app-secret --from-literal=DB_PASSWORD=pass123
```
### Verify
```bash
kubectl get secrets
kubectl describe secret app-secret
```
## Use Them in a Pod
```bash
kubectl edit deployment nginx-demo
```
```yaml
env:
- name: APP_COLOR
  valueFrom:
    configMapKeyRef:
      name: app-config
      key: APP_COLOR

- name: DB_PASSWORD
  valueFrom:
    secretKeyRef:
      name: app-secret
      key: DB_PASSWORD
```
## Verify Inside Pod
```bash
kubectl exec -it <pod-name> -- /bin/sh
```
### Print variables
```bash
printenv APP_COLOR
printenv DB_PASSWORD
```
