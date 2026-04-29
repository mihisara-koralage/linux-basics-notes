# Day 105 — RBAC

## Topics Covered
- Role vs ClusterRole
- RoleBinding vs ClusterRoleBinding
- Verbs: get, list, create, delete
- Least privilege permissions

## Commands

kubectl get roles -A
kubectl get clusterroles
kubectl auth can-i list pods --as=system:serviceaccount:dev:dev-user -n dev

## What I Learned
RBAC controls access in Kubernetes and helps apply least privilege securely.
