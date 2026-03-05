# Day 070 – Backup Automation & Scheduling

## 🎯 Objective
Automate Kubernetes backups using Velero schedule.

---

## 🧠 Why Automation?

- Manual backups are unreliable
- Production systems require automatic protection
- Backup must run even if no one is watching

---

## 🛠 Practical Done

Created scheduled backup:

velero schedule create daily-backup \
--schedule="0 2 * * *" \
--include-namespaces pv-test

Triggered manual backup from schedule:

velero backup create --from-schedule daily-backup

Verified backup status:

velero backup get

---

## 🔄 Retention Strategy

Used --ttl flag:

--ttl 168h  (7 days)

Prevents storage overload and manages backup lifecycle.

---

## 🚨 Production Best Practices

- Use multiple backup intervals (hourly/daily/weekly)
- Monitor backup success
- Store backups remotely
- Test restore regularly

---

## 🧠 Key Takeaway

Backup must be automated, monitored, and rotated.
Manual backup is not production-ready.
