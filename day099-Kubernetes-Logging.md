# Kubernetes Logging

Logs:
- Application logs
- Container logs
- Node logs

Problem:
Pods are temporary → logs lost

Solution:
Centralized logging

Stack:
- Fluentd (collect)
- Elasticsearch (store)
- Kibana (visualize)

Flow:
Pods → Fluentd → Elasticsearch → Kibana
