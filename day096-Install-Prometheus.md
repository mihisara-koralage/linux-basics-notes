# Prometheus Installation

Install using Helm:
helm repo add prometheus-community
helm install monitoring kube-prometheus-stack

Access:
kubectl port-forward svc/prometheus 9090:9090

Test:
Query: up

Purpose:
- Collect metrics
- Monitor cluster
