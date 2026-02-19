# Day 62 — GitOps and Argo CD

![GitOps](https://img.shields.io/badge/GitOps-Methodology-FC6D26?style=for-the-badge&logo=git&logoColor=white)
![ArgoCD](https://img.shields.io/badge/Argo%20CD-Deployment-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

---

## What is GitOps?

GitOps is a way of managing infrastructure and deployments where **Git is the single source of truth**.

Instead of running `kubectl apply` manually, you commit changes to Git — and a tool automatically syncs the cluster to match.

> "If it's not in Git, it doesn't exist."

---

## CI/CD vs GitOps

| | CI/CD (Push-based) | GitOps (Pull-based) |
|---|---|---|
| **Trigger** | Pipeline pushes to cluster | Cluster pulls from Git |
| **Access** | Pipeline needs cluster credentials | Cluster agent runs inside |
| **Source of truth** | Pipeline scripts | Git repository |
| **Drift detection** | None | Automatic |
| **Audit trail** | CI logs | Git history |
| **Rollback** | Re-run pipeline | `git revert` |

---

## How Argo CD Works

Argo CD runs **inside** your Kubernetes cluster and continuously watches a Git repo. When it detects a difference between what's in Git and what's running in the cluster, it syncs automatically.

```
Developer commits to Git
        │
        ▼
┌──────────────────┐
│   Git Repository │  deployment.yaml, values.yaml
│   (Source of     │  ← the desired state
│    Truth)        │
└────────┬─────────┘
         │  Argo CD watches for changes
         ▼
┌──────────────────┐
│    Argo CD       │  compares desired state (Git)
│    Controller    │  vs actual state (cluster)
│  (runs in K8s)   │
└────────┬─────────┘
         │  syncs automatically
         ▼
┌──────────────────┐
│  Kubernetes      │  cluster updated to match Git
│  Cluster         │
└──────────────────┘
         │
         │  if drift detected (manual change in cluster)
         ▼
    Argo CD corrects it back to Git state
```

---

## Benefits of GitOps

| Benefit | Why It Matters |
|---|---|
| 🔒 **Security** | Cluster credentials stay inside the cluster — not in CI pipelines |
| 📜 **Audit trail** | Every change is a Git commit with author, timestamp, message |
| ⏪ **Easy rollback** | `git revert` rolls back the entire deployment instantly |
| 🔁 **Drift correction** | Manual `kubectl` changes get auto-corrected back to Git state |
| 👁 **Visibility** | Argo CD UI shows live sync status of every app |

---

## Simple Architecture

```
┌─────────────┐     push      ┌──────────────────┐
│  Developer  │ ────────────► │  Git Repository  │
└─────────────┘               │  (Desired State) │
                              └────────┬─────────┘
                                       │  watched by
                                       ▼
                              ┌──────────────────┐
                              │    Argo CD       │
                              │  (inside cluster)│
                              └────────┬─────────┘
                                       │  applies
                                       ▼
                              ┌──────────────────┐
                              │   Kubernetes     │
                              │   Cluster        │
                              │  (Actual State)  │
                              └──────────────────┘
```

---

*[← Day 61 — CI/CD with Kubernetes](../day-61/) · [Day 63 →](../day-63/)*
