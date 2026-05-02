# Day 108 — Secrets Management

## Topics Covered
- Kubernetes Secrets
- Env vars vs mounted files
- Base64 is not encryption
- Secret rotation
- External secret managers

## Commands

kubectl get secrets -A
kubectl create secret generic db-secret --from-literal=username=admin --from-literal=password=StrongPass123

## What I Learned
Secrets should never be hardcoded. Kubernetes can manage them, but production security needs RBAC and stronger secret systems.
