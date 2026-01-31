# Day 48 – Volumes & Persistent Storage in Kubernetes
## Ephemeral storage problem
By default:
- When a Pod dies → its data is lost
- New Pod = new filesystem

This is not acceptable for:
- Databases
- Logs
- User uploads
## Volume vs PV vs PVC
### Kubernetes Volume
- Is attached to a Pod
- Shared by containers in the Pod
- Exists as long as the Pod exists
- If Pod is deleted → volume is gone.

### PersistentVolume (PV)
- Is a cluster-level storage resource
- Provisioned by admin or cloud provider
- Exists independently of Pods

Examples:
- AWS EBS
- GCE Persistent Disk
- NFS

### PersistentVolumeClaim (PVC)
- Is a request for storage
- Made by the user/app
- Binds to a PV automatically
## Storage flow diagram
```text
Pod
 |
PVC
 |
PV
 |
Storage (Disk / Cloud)
```
## Example: PVC YAML
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: app-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```
