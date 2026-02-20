# Day 63 — Kubernetes Security Basics

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Security](https://img.shields.io/badge/Security-Hardening-DC143C?style=for-the-badge&logo=shieldsdotio&logoColor=white)
![RBAC](https://img.shields.io/badge/RBAC-Access%20Control-2E8B57?style=for-the-badge&logo=lockr&logoColor=white)

---

## What is RBAC?

**Role-Based Access Control** — controls *who* can do *what* inside a Kubernetes cluster.

```
Who?          →   User / ServiceAccount
Can do what?  →   Role (get, list, create, delete...)
On what?      →   Resource (pods, secrets, deployments...)
```

Three core pieces:

| Object | Purpose |
|---|---|
| `Role` | Defines allowed actions on resources (namespace-scoped) |
| `ClusterRole` | Same, but cluster-wide |
| `RoleBinding` | Attaches a Role to a user or ServiceAccount |

```yaml
# Example: allow reading pods only
kind: Role
rules:
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["get", "list"]
```

---

## Service Accounts

Every pod runs as a **ServiceAccount** — its identity inside the cluster.

```
Pod  →  ServiceAccount  →  Role  →  Permissions
```

- Default service account has too many permissions — always create a dedicated one
- Mount only the token your pod actually needs
- Never share service accounts across unrelated workloads

```yaml
spec:
  serviceAccountName: my-app-sa   # use a dedicated SA, not default
```

---

## Why Not Run as Root?

If a container runs as root and gets compromised, the attacker has root-level access to the node.

```yaml
# Always set this in your pod spec
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
```

> A container doesn't need root to serve web traffic, run a worker, or process a queue. Default to least privilege.

---

## Secrets Best Practices

Kubernetes Secrets are **base64-encoded, not encrypted** by default.

| Practice | Why |
|---|---|
| Never hardcode secrets in images | Anyone who pulls the image sees them |
| Mount as volume, not env var | Env vars appear in crash logs & `kubectl describe` |
| Enable encryption at rest | Protects etcd from direct access |
| Use external secret stores | HashiCorp Vault, AWS Secrets Manager, Sealed Secrets |
| Restrict Secret access via RBAC | Not every pod should read every secret |

---

## Namespace Isolation

Namespaces are not a security boundary by default — but combined with **NetworkPolicy and RBAC**, they become one.

```
┌─────────────────────────────────────┐
│            Cluster                  │
│  ┌──────────────┐ ┌──────────────┐  │
│  │  namespace:  │ │  namespace:  │  │
│  │     dev      │ │    prod      │  │
│  │              │ │              │  │
│  │  own RBAC    │ │  own RBAC    │  │
│  │  own Network │ │  own Network │  │
│  │  Policy      │ │  Policy      │  │
│  └──────────────┘ └──────────────┘  │
└─────────────────────────────────────┘
```

- Dev pods cannot reach prod pods if NetworkPolicy blocks it
- Dev teams cannot access prod secrets if RBAC is configured correctly

---

## Image Security Basics

Your container image is your attack surface.

| Practice | What It Does |
|---|---|
| Use minimal base images | `alpine` or `distroless` — fewer packages, fewer vulnerabilities |
| Pin image versions | `nginx:1.25.3` not `nginx:latest` |
| Scan images in CI | Tools: Trivy, Snyk, Docker Scout |
| Never store secrets in images | They persist in image layers even if deleted |
| Use trusted registries | Avoid pulling random public images |

---

## Key Takeaways

```
✅  RBAC limits what every user and pod can do
✅  Service accounts give pods a least-privilege identity
✅  Never run containers as root
✅  Secrets need RBAC + encryption + external stores
✅  Namespaces + NetworkPolicy = workload isolation
✅  Small, pinned, scanned images reduce attack surface
```

---

*[← Day 62 — GitOps and Argo CD](../day-62/) · [Day 64 →](../day-64/)*
