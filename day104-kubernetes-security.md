# Day 104 — Kubernetes Security Fundamentals

## Topics Covered
- Kubernetes attack surface
- Least privilege principle
- Namespaces for isolation
- Container security basics
- kubeconfig access risks
- etcd security concepts

## Key Risks
- cluster-admin misuse
- default service accounts
- root containers
- exposed secrets
- unrestricted networking

## Commands

kubectl get ns
kubectl get pods -A
kubectl config get-contexts
kubectl describe pod <pod> -n <ns>

## What I Learned
Security in Kubernetes starts with access control, workload hardening, and isolation.
