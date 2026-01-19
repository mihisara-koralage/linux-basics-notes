# Day 12 – Linux Processes and Services

## What is a Process?
A process is a program that is currently running on the system.
Every time a command or application runs, it becomes a process.

Each process has:
- A Process ID (PID)
- An owner (user)
- A state (running, sleeping, stopped)

Example commands:
```
ps
ps aux
```
## Foreground and Background Processes
### Foreground Process
A foreground process runs in the terminal and blocks it until the process finishes.

Example:
```
sleep 10
```
### Background Process
A background process runs without blocking the terminal.

Example:
```
sleep 100 &
```
- jobs : Check background jobs

## What is a Service?
A service is a long-running background process that is managed by the system.
Services are used for applications that must keep running continuously.

Examples of services:
- SSH server
- Web server (nginx)
- Database server

Services do not depend on a terminal and can restart automatically if they fail.

## systemd and systemctl
Linux uses systemd to manage services.
The systemctl command is used to control services.

Common commands:
```
systemctl status service-name
sudo systemctl start service-name
sudo systemctl stop service-name
sudo systemctl restart service-name
```
## Services and System Boot
Some services are configured to start automatically when the system boots.

Enable a service on boot:
```
sudo systemctl enable service-name
```

Disable a service on boot:
```
sudo systemctl disable service-name
```
Starting services on boot is important so that servers continue working after restarts.

## Why This Matters in DevOps
Processes and services are critical in DevOps because:
- Servers must run applications 24/7
- Services need to restart automatically after failure
- Applications must start after system reboots
DevOps engineers manage and monitor services to keep systems reliable.

## Practical Commands Used
```
ps aux
jobs
systemctl status ssh
systemctl start ssh
systemctl enable ssh
```
## What I Practiced
- Viewing running processes
- Understanding foreground and background execution
- Managing services using systemctl
- Learning how services start on system boot
