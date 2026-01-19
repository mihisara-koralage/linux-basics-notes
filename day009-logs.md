# Day 9 – Linux Logs & Troubleshooting

## What are logs?
Logs are records of system and application events. They help system administrators
and DevOps engineers monitor system behavior, detect errors, and troubleshoot issues.

## Important Linux Log Locations
Most Linux system logs are stored inside the `/var/log` directory.

- /var/log/syslog   – General system activity logs
- /var/log/auth.log – Authentication and login-related logs (SSH, sudo)
- /var/log/kern.log – Kernel-related messages
- /var/log/boot.log – System boot logs

## Viewing Logs
Logs can be very large, so special commands are used to read them safely.

- less /var/log/syslog – View logs page by page
- tail /var/log/syslog – View last few lines
- tail -f /var/log/syslog – Monitor logs in real time

## journalctl
Modern Linux systems use systemd, which stores logs in a journal.
The `journalctl` command is used to view these logs.

- journalctl – View all system logs
- journalctl -xe – View recent errors and warnings
- journalctl -u ssh – View logs for the SSH service
- journalctl --since "10 minutes ago" – View recent logs

## Why Logs Matter in DevOps
Logs are essential for:
- Troubleshooting server and application issues
- Monitoring system health
- Debugging failed deployments
- Security auditing and incident investigation

DevOps engineers rely heavily on logs in production environments.

## What I Practiced
- Navigating the /var/log directory
- Reading system logs using less and tail
- Monitoring logs in real time
- Using journalctl to analyze service logs
