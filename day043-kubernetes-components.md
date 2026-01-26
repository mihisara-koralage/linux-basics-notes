# Day 43 – Kubernetes Core Components
## Cluster, Node, Pod
### A Kubernetes Cluster is:
- A group of machines
- Managed together
- Running containerized applications

A cluster has:
- Control Plane (the brain)
- Worker Nodes (do the work)

### A Node is:
- A VM or physical server
- Where containers actually run

Each node contains:
- Container runtime (Docker / containerd)
- kubelet (agent)
- kube-proxy (networking)

### A Pod is:
- The smallest unit in Kubernetes
- One or more containers
- Shared network & storage

Key points:
- Containers in a pod share:
  - IP address
  - Ports
  - Volumes
- Usually 1 container per pod
## Control Plane overview
The Control Plane decides:
- What runs
- Where it runs
- When it restarts

Main components (conceptual only):

- API Server
  - Entry point to Kubernetes
  - All commands go through here

- Scheduler
  - Chooses which node runs a pod

- Controller Manager
  - Watches the cluster
  - Fixes problems (self-healing)

- etcd
  - Key-value store
  - Stores cluster state
## How components interact
### Kubernetes High-Level Diagram
```text
            Kubernetes Cluster
        +------------------------+
        |                        |
        |   Control Plane        |
        |  +------------------+  |
        |  | API Server       |  |
        |  | Scheduler        |  |
        |  | Controllers      |  |
        |  | etcd             |  |
        |  +------------------+  |
        |                        |
        |   Worker Nodes         |
        |  +---------+ +-------+ |
        |  | Node 1  | | Node 2| |
        |  |  Pod    | |  Pod  | |
        |  +---------+ +-------+ |
        +------------------------+
```
### Request Flow
```text
User
 |
 v
API Server
 |
 v
Scheduler
 |
 v
Node
 |
 v
Pod
 |
 v
Container
```
