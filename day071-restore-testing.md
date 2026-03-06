# Day 071 – Restore Testing & Disaster Simulation

## Objective
Test Kubernetes backup recovery using Velero restore.

---

## Why Restore Testing Matters

A backup is useless if restore fails.

Production systems require regular disaster recovery testing.

---

## Practical Performed

1. Verified existing backups
2. Deleted namespace `pv-test`
3. Simulated application environment loss
4. Restored from Velero backup
5. Verified namespace and resources were recreated

---

## Restore Command

velero restore create --from-backup daily-backup

Checked status with:

velero restore get

---

## Recovery Verification

kubectl get ns  
kubectl get all -n pv-test

Confirmed environment was restored successfully.

---

## Production Insight

Disaster recovery should be tested regularly.

Common restore strategies:

- Partial restore (single namespace)
- Full cluster restore

---

## Key Takeaway

Backup creation is only half of disaster recovery.

Restore validation completes the recovery strategy.
