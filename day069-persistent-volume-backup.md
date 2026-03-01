# Day 069 – Persistent Volume Backup Basics

## 🎯 Objective
Understand why cluster state backup is not enough and how to protect application data.

---

## 🧠 Key Learning

- etcd stores configuration only
- Persistent Volumes store real data
- Pod deletion does not delete PV data
- Application data requires separate backup strategy

---

## 🛠 Practical Done

1. Created namespace `pv-test`
2. Created PersistentVolumeClaim
3. Created pod using PVC
4. Wrote data into /data/test.txt
5. Deleted pod
6. Recreated pod
7. Verified data persisted

---

## 🔐 Backup Strategies

1. Application-level backup (mysqldump, pg_dump)
2. VolumeSnapshot API
3. Velero with volume backup

---

## 🚨 Production Insight

- etcd snapshot does NOT protect database data
- Volume snapshot is commonly used in cloud environments
- Always test restore process

---

## 🧠 Key Takeaway

Cluster recovery ≠ Data recovery

Both must be planned separately.
