# Grafana Dashboards

Access:
- kubectl port-forward svc/monitoring-grafana -n monitoring 3000:80
- kubectl get secret --namespace monitoring monitoring-grafana -o jsonpath="{.data.admin-password}" | bas
e64 --decode ; echo

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
