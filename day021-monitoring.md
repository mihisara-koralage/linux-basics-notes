# Day 21: Monitoring & Automating System Health Checks
## Disk monitoring script
Create:
```
nano monitor_disk.sh
```
```
#!/bin/bash
LOG_FILE=/home/mihisara/logs/disk_usage.log
THRESHOLD=80

usage=$(df -h / | awk 'NR==2 {print $5}' | sed 's/%//')
date=$(date '+%Y-%m-%d %H:%M:%S')

if [ "$usage" -gt "$THRESHOLD" ]; then
  echo "$date WARNING: Disk usage is above $THRESHOLD%" >> $LOG_FILE
else
  echo "$date Disk usage is normal" >> $LOG_FILE
fi
```
## Cron schedule example
Run every hour:
```
crontab -e
0 * * * * /home/mihisara/scripts/monitor_disk.sh
```
Output will be saved in /home/mihisara/logs/disk_usage.log.

## Optional CPU/memory script
```
#!/bin/bash
LOG_FILE=/home/mihisara/logs/cpu_mem.log
CPU=$(top -bn1 | grep "Cpu(s)" | awk '{print $2 + $4}')
MEM=$(free -m | awk 'NR==2{printf "%s", $3/$2 * 100}')

date=$(date '+%Y-%m-%d %H:%M:%S')
echo "$date CPU: $CPU% MEM: $MEM%" >> $LOG_FILE
```
## Why monitoring matters in DevOps
- Scripts like these are the foundation for monitoring tools like Nagios, Zabbix, Prometheus
- Writing your own scripts helps you understand how tools work internally
- Combined with alerts, these scripts can notify teams automatically
