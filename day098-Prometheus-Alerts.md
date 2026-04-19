# Prometheus Alerts

Components:
- Prometheus (rules)
- AlertManager (notifications)

Steps:
1. Create PrometheusRule
2. Apply YAML
3. Check Prometheus Alerts
4. Trigger condition

Example:
Pod restart alert

States:
- Pending
- Firing
- Resolved

-  kubectl port-forward svc/monitoring-kube-prometheus-alertmanager -n monitoring 9093:9093
