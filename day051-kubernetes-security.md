# Day 51 – Kubernetes Security Basics
## Why security matters
A cluster can:
- Deploy apps
- Access secrets
- Delete workloads
- Change configs

Without security:
- Anyone could break production
- Secrets could leak
- Accidental deletions happen
## What is RBAC?
RBAC = Role-Based Access Control

It controls:
- Who can do what
- On which resources
- In which namespace
## Role vs RoleBinding
### Role
Defines permissions.

Example:
- Read pods
- List services
- Cannot delete
### RoleBinding
Connects:
- User → Role

Think:
- RoleBinding = gives permission to someone
## Least privilege concept
Give only needed access.

Example:
- Developer can view pods
- Developer cannot delete cluster

Why?
- Prevent mistakes
- Improve security
- Limit damage
## Example YAML
Role:
```yaml
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: dev
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list"]
```
RoleBinding:
```yaml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: read-pods
  namespace: dev
subjects:
- kind: User
  name: dev-user
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```
