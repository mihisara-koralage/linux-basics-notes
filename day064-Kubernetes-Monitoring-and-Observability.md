# Day 64 — Kubernetes Monitoring and Observability

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

---

## What is Monitoring?

Monitoring is knowing **what your system is doing right now** — and being alerted when something goes wrong before users notice.

> You can't fix what you can't see.

---

## Metrics vs Logs vs Traces

| Pillar | What it answers | Example |
|---|---|---|
| 📊 **Metrics** | How much / how many? | CPU 85%, 200 req/s |
| 📄 **Logs** | What happened and when? | `ERROR: DB connection failed` |
| 🔍 **Traces** | Where did the request go? | API → Auth → DB → timeout |

Together these three form the **observability stack** for any production system.

---

## Prometheus

Prometheus **scrapes metrics** from your pods and stores them as time-series data.

```
Pods expose /metrics endpoint
        │
        ▼
  Prometheus scrapes every 15s
        │
        ▼
  Stores time-series data
        │
        ▼
  Query with PromQL
```

```yaml
# Pod tells Prometheus to scrape it
annotations:
  prometheus.io/scrape: "true"
  prometheus.io/port: "8080"
```

---

## Grafana

Grafana **visualises** the data Prometheus collects — turning raw numbers into dashboards.

```
Prometheus (data)  →  Grafana (dashboards)  →  Team sees graphs
```

- CPU / memory usage over time
- Pod restarts, error rates, request latency
- Set visual thresholds that trigger alerts

---

## ELK Stack

For **logs**, the standard stack is ELK:

```
Elasticsearch  — stores and indexes logs
Logstash       — collects and transforms logs
Kibana         — searches and visualises logs
```

```
Pod logs  →  Logstash  →  Elasticsearch  →  Kibana UI
```

Search across thousands of pods in one place instead of running `kubectl logs` on each one.

---

## Why Alerting Matters

Dashboards need humans watching them. Alerts fire **automatically** when thresholds are crossed.

| Without Alerts | With Alerts |
|---|---|
| Someone notices hours later | Team notified in seconds |
| Users report the outage first | Engineers fix before users notice |
| Manual dashboard watching | Automated, rule-based detection |

---

## Production Architecture

```
┌──────────────────────────────────────────────┐
│               Kubernetes Cluster             │
│                                              │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐       │
│  │  Pod A  │  │  Pod B  │  │  Pod C  │       │
│  │/metrics │  │/metrics │  │  logs   │       │
│  └────┬────┘  └────┬────┘  └────┬────┘       │
│       │            │            │            │
│       ▼            ▼            ▼            │
│  ┌──────────┐             ┌──────────┐       │
│  │Prometheus│             │Logstash  │       │
│  │(metrics) │             │(logs)    │       │
│  └────┬─────┘             └────┬─────┘       │
│       │                        │             │
└───────┼────────────────────────┼─────────────┘
        ▼                        ▼
   ┌─────────┐            ┌─────────────┐
   │ Grafana │            │Elasticsearch│
   │Dashboard│            │  + Kibana   │
   └────┬────┘            └─────────────┘
        │
        ▼
   ┌─────────┐
   │ Alerts  │ → Slack / PagerDuty / Email
   └─────────┘
```

---

## Key Takeaways

```
✅  Metrics → Prometheus    (numbers over time)
✅  Visualisation → Grafana (dashboards + alerts)
✅  Logs → ELK Stack        (search across all pods)
✅  Alerting = proactive, not reactive
✅  Observability is not optional in production
```

---

*[← Day 63 — Kubernetes Security](../day-63/) · [Day 65 →](../day-65/)*
