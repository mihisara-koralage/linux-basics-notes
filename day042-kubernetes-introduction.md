# Day 42 – Kubernetes Basics: What & Why
## Why Kubernetes exists
Docker is great, but in production, problems appear:

### Problems with Docker-only setups
- What if a container crashes?
- How do you run 10 replicas?
- How do you update without downtime?
- How do containers find each other?
- What if one server goes down?

Docker does not solve these automatically.
### This is why Kubernetes exists
- Kubernetes is a container orchestrator.
- It manages containers for you, automatically.
### What Kubernetes Does
- Runs containers across many machines
- Restarts containers if they crash
- Scales apps up/down
- Distributes traffic
- Handles rolling updates
- Keeps desired state running
## Docker vs Kubernetes
| Docker                   | Kubernetes         |
| ------------------------ | ------------------ |
| Runs containers          | Manages containers |
| Single machine (usually) | Multiple machines  |
| Manual scaling           | Auto scaling       |
| Manual recovery          | Self-healing       |

## What orchestration means
```It manages containers for you, automatically.```
## High-level components
- Cluster
  - A group of machines (nodes)

- Node
  - A machine (VM or physical)
  - Runs containers

- Control Plane
  - Decides what should run where
  - Watches health
  - Maintains desired state
