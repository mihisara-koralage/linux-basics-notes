# Day 103 — LogQL Queries + Real Log Analysis

## What is LogQL?

LogQL is **Loki Query Language** used to search, filter, and analyze logs.

---

## Basic Queries

| Purpose | Query |
|---|---|
| Show all logs | `{}` |
| Filter by namespace | `{namespace="default"}` |
| Filter by pod | `{pod="log-demo"}` |

---

## Search Logs

```logql
# Find keyword
{namespace="default"} |= "error"

# Exclude keyword
{namespace="default"} != "healthcheck"

# Regex search
{namespace="default"} |~ "500|404|timeout"
```

---

## Metrics from Logs

```logql
# Count logs in 5 min
count_over_time({namespace="default"}[5m])

# Count errors
count_over_time({namespace="default"} |= "error"[5m])
```

---

## Real Use Cases

- 🔴 Find application errors
- 💥 Investigate pod crashes
- 🌐 Detect HTTP 500 issues
- 📢 Analyze noisy pods
- 🐛 Debug production incidents

---

## What I Learned

- **Labels** help narrow searches
- **Filters** make troubleshooting faster
- **Logs can generate metrics**
- **LogQL** is powerful for observability
