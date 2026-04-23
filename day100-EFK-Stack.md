# EFK Stack

Components:
- Elasticsearch (storage)
- Fluentd (collector)
- Kibana (UI)

Flow:
Pods → Fluentd → Elasticsearch → Kibana

Steps:
1. Install Elasticsearch
2. Install Kibana
3. Install Fluentd
4. View logs in Kibana

- kubectl port-forward svc/kibana-kibana -n logging 5601:5601
- kubectl get secret elasticsearch-master-credentials -n logging -o jsonpath="{.data.password}" | base64 -d
