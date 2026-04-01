# Day 073 – Pod Anti-Affinity & Node-Level High Availability

## 🎯 Objective
Ensure replicas are spread across nodes to prevent single-node failure.

---

## 🧠 Problem

Replicas may be scheduled on same node.

Node failure can bring entire application down.

Replicas alone do not guarantee high availability.

---

## 🛠 Solution: Pod Anti-Affinity

Pod Anti-Affinity spreads pods across nodes.

Uses:

topologyKey: kubernetes.io/hostname

---

## 🛠 Practical

Created deployment with anti-affinity rules.

replicas: 3

Scheduler attempts to place pods on different nodes.

---

## 🧠 How It Works

- Scheduler checks labels
- Avoids placing same pods on same node
- Improves resilience against node failure

---

## 🚨 Production Insight

Used in multi-node clusters for real high availability.

Often combined with:

- multi-zone clusters
- load balancer
- replicas

---

## 🧠 Key Takeaway

Replicas provide self-healing  
Anti-affinity provides node-level resilience
