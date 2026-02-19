# Day 61 — CI/CD with Kubernetes

![CI/CD](https://img.shields.io/badge/CI%2FCD-Automation-6e40c9?style=for-the-badge&logo=githubactions&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

## What is CI/CD?

**CI (Continuous Integration)** — automatically build and test code every time a developer pushes a change.

**CD (Continuous Delivery/Deployment)** — automatically deliver that tested code all the way to production.

> The goal: eliminate manual steps between writing code and running it in production.

---

## Full Deployment Flow

```
Developer pushes code
        │
        ▼
┌─────────────────┐
│   Git Repository│  (e.g. GitHub)
└────────┬────────┘
         │  triggers
         ▼
┌─────────────────┐
│   CI Pipeline   │  lint → test → build
│ (GitHub Actions)│
└────────┬────────┘
         │  on success
         ▼
┌─────────────────┐
│  Docker Build   │  docker build -t myapp:v2 .
│  & Push to      │  docker push registry/myapp:v2
│  Registry       │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   CD Pipeline   │  kubectl set image /
└────────┬────────┘  helm upgrade
         │
         ▼
┌─────────────────┐
│   Kubernetes    │  rolling update → new pods live
│   Cluster       │
└─────────────────┘
```

---

## How Docker Connects

Docker is the **packaging layer** between your code and Kubernetes.

```
Source Code  →  Dockerfile  →  Image  →  Registry  →  K8s pulls & runs it
```

Every CI run produces a **new versioned image** (e.g. `myapp:v2`). Kubernetes then pulls that exact image — no environment surprises, no "works on my machine."

---

## How Kubernetes Updates Pods

When CD triggers a deployment update, Kubernetes performs a **rolling update** by default:

```
Old pods:  [v1] [v1] [v1]
                │
                ▼  kubectl set image / helm upgrade
                │
New pods:  [v2] [v2] [v2]   ← spun up one by one
Old pods:  terminated only after new ones are healthy
```

Zero downtime. If something breaks → `kubectl rollout undo` reverts instantly.

---

## Why Automation Matters

| Manual | Automated (CI/CD) |
|---|---|
| Error-prone deployments | Consistent, repeatable builds |
| Hours to ship a fix | Minutes from push to production |
| "Works on my machine" | Identical environments every time |
| No safety net | Automatic rollback on failure |
| One person knows the process | Process lives in code, anyone can run it |

---

*[← Day 60 — Helm Advanced](../day-60/) · [Day 62 →](../day-62/)*
