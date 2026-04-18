# Grafana Dashboards

Access:
kubectl port-forward svc/monitoring-grafana -n monitoring 3000:80

Login:
admin / password from secret

Features:
- Dashboards
- Graphs
- Metrics visualization

Data Source:
Prometheus

Example queries:
- up
- node_cpu_seconds_total
