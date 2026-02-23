# Day 65 — High Availability and Reliability

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Reliability](https://img.shields.io/badge/Reliability-HA%20Design-2E8B57?style=for-the-badge&logo=statuspage&logoColor=white)

---

## What is High Availability?

**High Availability (HA)** means your app keeps running even when something fails — a pod crashes, a node goes down, a deployment rolls out.

> The goal: eliminate single points of failure.

---

## Why Replicas Matter

One pod = one point of failure. Multiple replicas spread across nodes means one dying doesn't take the app down.

```
1 replica:   [Pod]              ← dies = outage

3 replicas:  [Pod] [Pod] [Pod]  ← one dies, two serve traffic
```

```yaml
spec:
  replicas: 3        # always run at least 2-3 in production
```

---

## RollingUpdate vs Recreate

| Strategy | What happens | Use when |
|---|---|---|
| `RollingUpdate` | New pods come up before old ones go down | Production — zero downtime |
| `Recreate` | All old pods killed, then new ones created | Dev — simpler, causes brief downtime |

```yaml
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 1   # max pods down at once
    maxSurge: 1         # max extra pods during update
```

---

## Liveness vs Readiness

| Probe | Question it answers | On failure |
|---|---|---|
| **Liveness** | Is the pod still alive? | Kubernetes restarts it |
| **Readiness** | Is the pod ready for traffic? | Removed from Service endpoints |

```yaml
livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 5

readinessProbe:
  httpGet:
    path: /ready
    port: 8080
  initialDelaySeconds: 3
```

> Both together = self-healing pods that never receive traffic before they're ready.

---

## PodDisruptionBudget

A **PDB** sets the minimum number of pods that must stay running during voluntary disruptions — node drains, cluster upgrades, scaling events.

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: my-app-pdb
spec:
  minAvailable: 2      # at least 2 pods must stay up
  selector:
    matchLabels:
      app: my-app
```

```
3 replicas running + PDB minAvailable: 2
→ Kubernetes will only evict 1 pod at a time
→ App stays live during node maintenance
```

---

## Why Multi-Node Matters

Spreading pods across nodes means a single node failure doesn't take everything down.

```
Single node:                    Multi-node:
┌────────────────┐              ┌──────────┐  ┌──────────┐  ┌──────────┐
│ Node A         │              │ Node A   │  │ Node B   │  │ Node C   │
│ [Pod][Pod][Pod]│              │ [Pod]    │  │ [Pod]    │  │ [Pod]    │
└───────┬────────┘              └────┬─────┘  └──────────┘  └──────────┘
        │ fails                      │ fails
        ▼                            ▼
    total outage               2 pods still serve traffic
```

Use `podAntiAffinity` to tell Kubernetes to spread replicas across nodes.

---

## Key Takeaways

```
✅  Always run 2+ replicas in production
✅  RollingUpdate = zero-downtime deployments
✅  Liveness restarts broken pods automatically
✅  Readiness keeps traffic away from unready pods
✅  PDB protects availability during maintenance
✅  Spread pods across nodes to survive node failures
```

---

*[← Day 64 — Monitoring and Observability](../day-64/) · [Day 66 →](../day-66/)*
