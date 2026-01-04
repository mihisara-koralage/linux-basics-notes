# Day 20: Task Scheduling with Cron
## What cron is
Cron is a Linux scheduler.

It runs:
- Scripts
- Commands
- Jobs
  
automatically at fixed times or intervals

Examples:
- Daily backups
- Log cleanup
- Health checks
- Monitoring scripts

## Crontab format explanation
~~~
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week (0–6)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
~~~
## Example schedules
| Schedule    | Meaning       |
| ----------- | ------------- |
| `* * * * *` | Every minute  |
| `0 * * * *` | Every hour    |
| `0 2 * * *` | Daily at 2 AM |
| `0 0 * * 0` | Every Sunday  |

## Disk check cron example
Run disk check every day at 9 AM:
~~~
0 9 * * * /home/mihisara/scripts/check_disk.sh
~~~
## Why cron matters in DevOps
Cron is used for:
- Automated backups
- Monitoring checks
- Cleanup jobs
- Scheduled deployments (legacy systems)

Even modern cloud tools still rely on cron concepts.
