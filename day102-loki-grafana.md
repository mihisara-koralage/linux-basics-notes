# Day 101 — Loki + Grafana Connection Fix 🔥

## Issue
Grafana showed:

Unable to connect with Loki. Please check the server logs for more details.

## Root Cause
Grafana version compatibility / datasource validation issue.

Loki backend was healthy, but old Grafana UI failed connection test.

## Verification Commands

```bash
kubectl exec -n monitoring monitoring-grafana-86466f76-vn24t -c grafana -- curl http://loki:3100/ready
```
