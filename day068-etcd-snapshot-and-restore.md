# Day 068 – etcd Snapshot & Restore

![Kubernetes Badge](https://img.shields.io/badge/Kubernetes-1.21.0-informational?style=flat-square) 
![etcd Badge](https://img.shields.io/badge/etcd-3.5.0-orange?style=flat-square) 
![Backup Badge](https://img.shields.io/badge/Backup-Enabled-brightgreen?style=flat-square)

---

## 🎯 Objective
Understand how to backup and restore Kubernetes cluster state using etcd snapshot.

---

## 🧠 What is etcd Snapshot?

- Point-in-time backup of cluster state
- Stored as snapshot.db
- Contains Kubernetes objects
- Does NOT contain application data

---

## 🛠 Snapshot Command

ETCDCTL_API=3 etcdctl snapshot save snapshot.db

Production version includes:
- --endpoints
- --cacert
- --cert
- --key

---

## 🔍 Verify Snapshot

ETCDCTL_API=3 etcdctl snapshot status snapshot.db

---

## 🔄 Restore Process Overview

1. Stop control plane
2. Restore snapshot
3. Replace etcd data directory
4. Restart services

Restore command:

ETCDCTL_API=3 etcdctl snapshot restore snapshot.db --data-dir=/var/lib/etcd-restore

---

## 🚨 Production Notes

- Store backups offsite
- Encrypt backups
- Automate daily snapshot
- Test restore regularly

---

## 🧠 Key Takeaways

- etcd = cluster brain
- Snapshot = cluster configuration backup
- Persistent volumes are NOT included
- Restore requires control plane restart

---

## 💬 Interview Question I Can Answer

How would you recover a self-managed Kubernetes cluster if etcd is corrupted?
