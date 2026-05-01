# Day 107 — Network Policies

## Topics Covered
- Pod firewall rules
- Ingress vs Egress
- Default deny model
- Allow specific pod communication
- Namespace isolation

## Commands

kubectl get networkpolicy -A
kubectl apply -f default-deny.yaml
kubectl apply -f allow-frontend-backend.yaml

## What I Learned
Network Policies secure Kubernetes networking by allowing only approved pod traffic.
