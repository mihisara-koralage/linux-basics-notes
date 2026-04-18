# Prometheus Installation

Install using Helm:
helm repo add prometheus-community
helm install monitoring kube-prometheus-stack

Access:
- kubectl port-forward svc/monitoring-kube-prometheus-prometheus -n monitoring 9090:9090

Test:
Query: up

Purpose:
- Collect metrics
- Monitor cluster
