# Day 66 — Disaster Recovery and Backup Strategies

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Velero](https://img.shields.io/badge/Velero-Backup-00BFFF?style=for-the-badge&logo=fastly&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-Storage-C72E49?style=for-the-badge&logo=minio&logoColor=white)

---

## What is Disaster Recovery?

**Disaster Recovery (DR)** is the plan for restoring your system after a catastrophic failure — corrupted cluster, accidental deletion, cloud outage, or data loss.

> HA keeps you running. DR gets you back when everything breaks.

---

## RPO vs RTO

| | Definition | Example |
|---|---|---|
| **RPO** — Recovery Point Objective | Max acceptable data loss | RPO = 10 min → backup every 10 min |
| **RTO** — Recovery Time Objective | Max acceptable downtime | RTO = 30 min → must recover within 30 min |

---

## HA vs Disaster Recovery

| High Availability | Disaster Recovery |
|---|---|
| Prevents downtime | Recovers from downtime |
| Replicas + probes | Backups + restore process |
| Handles pod/node failures | Handles cluster-level failures |

---

## What Needs Backup in Kubernetes

```
Cluster State    →  etcd
Workloads        →  Deployments, StatefulSets, DaemonSets
Networking       →  Services, Ingress
Configuration    →  ConfigMaps, Secrets
Storage          →  PersistentVolumes, PVCs
Namespaces       →  all resource scopes
Databases        →  application data (separate backup strategy)
```

---

## Tools

**Velero** — the standard Kubernetes backup and restore tool. Backs up cluster resources and PVs to object storage.

**MinIO** — S3-compatible object storage, used locally in labs as the backup destination.

```
Velero  →  snapshots cluster state  →  stores in MinIO / S3
```

---

## Practical Implementation

### Step 1 — Install Velero CLI

```bash
# Download specific release from GitHub
wget https://github.com/vmware-tanzu/velero/releases/download/v1.13.0/velero-v1.13.0-linux-amd64.tar.gz
tar -xvf velero-v1.13.0-linux-amd64.tar.gz
mv velero-v1.13.0-linux-amd64/velero /usr/local/bin/
velero version
```

### Step 2 — Deploy MinIO

```bash
kubectl create namespace velero

kubectl apply -f - <<EOF
apiVersion: apps/v1
kind: Deployment
metadata:
  name: minio
  namespace: velero
spec:
  replicas: 1
  selector:
    matchLabels:
      app: minio
  template:
    spec:
      containers:
      - name: minio
        image: minio/minio
        args: ["server", "/data"]
        env:
        - name: MINIO_ROOT_USER
          value: "minio"
        - name: MINIO_ROOT_PASSWORD
          value: "minio123"
EOF
```

### Step 3 — Install Velero in Cluster

```bash
velero install \
  --provider aws \
  --plugins velero/velero-plugin-for-aws:v1.9.0 \
  --bucket velero-backups \
  --secret-file ./credentials-velero \
  --use-volume-snapshots=false \
  --backup-location-config \
    region=minio,s3ForcePathStyle=true,s3Url=http://minio.velero.svc:9000
```

### Step 4 — Create Test Workload

```bash
kubectl create namespace test-app
kubectl create deployment nginx --image=nginx -n test-app
kubectl expose deployment nginx --port=80 --type=NodePort -n test-app
kubectl get all -n test-app
```

### Step 5 — Create Backup

```bash
# Backup entire namespace
velero backup create test-backup --include-namespaces test-app

# Check backup status
velero backup describe test-backup
velero backup get
```

### Step 6 — Simulate Disaster

```bash
# Delete the namespace entirely
kubectl delete namespace test-app

# Confirm it's gone
kubectl get ns
```

### Step 7 — Restore

```bash
# Restore from backup
velero restore create --from-backup test-backup

# Verify restore
velero restore get
kubectl get all -n test-app
```

---

## Recovery Flow

```
Normal state: workloads running
        │
        │  velero backup create
        ▼
Backup stored in MinIO / S3
        │
        │  disaster strikes (deletion / corruption)
        ▼
Cluster state lost
        │
        │  velero restore create --from-backup
        ▼
Workloads restored to pre-disaster state
```

---

## Key Takeaways

```
✅  RPO defines how often to backup
✅  RTO defines how fast you must recover
✅  Velero backs up both K8s resources and PVs
✅  Test your restore — a backup you've never restored is untested
✅  Store backups outside the cluster (S3, MinIO, GCS)
✅  DR complements HA — you need both in production
```

---

*[← Day 65 — High Availability](../day-65/) · [Day 67 →](../day-67/)*
