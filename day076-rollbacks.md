# Day 076 – Kubernetes Rollbacks

## 🎯 Objective

Learn how to revert failed deployments.

---

## 🧠 Problem

New deployment may introduce bugs.

Need ability to revert quickly.

---

## 🔄 Rollback

Kubernetes stores deployment revisions.

Rollback restores previous version.

---

## 🛠 Practical

Checked history:

kubectl rollout history deployment/rolling-demo

Rollback:

kubectl rollout undo deployment/rolling-demo

Rollback to specific revision:

kubectl rollout undo deployment/rolling-demo --to-revision=1

---

## 🧠 Key Takeaway

Rollback allows instant recovery from failed deployments.
