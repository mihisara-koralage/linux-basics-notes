# Day 106 — Service Accounts

## Topics Covered
- Pod identity in Kubernetes
- Default vs custom service accounts
- Mounted tokens
- Service accounts with RBAC
- Security best practices

## Commands

kubectl get sa -A
kubectl create serviceaccount app-reader -n app-dev
kubectl auth can-i list pods --as=system:serviceaccount:app-dev:app-reader -n app-dev

## What I Learned
Service accounts give pods identities, while RBAC controls what those identities can access.
