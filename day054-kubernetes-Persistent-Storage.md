# Day 54 — Persistent Storage in Kubernetes
## Create pvc.yaml
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: nginx-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```
## Apply it
```bash
kubectl apply -f pvc.yaml
```
Check:
```bash
kubectl get pvc
```
## Attach PVC to Deployment
```bash
kubectl edit deployment nginx-demo
```
```yaml
volumes:
- name: nginx-storage
  persistentVolumeClaim:
    claimName: nginx-pvc
```
## Why PVC important?
Without it:
- Databases lose data
- Apps reset
- Not production-ready
