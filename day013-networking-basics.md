# Day 13 – Linux Networking Basics

## What is Networking?
Networking allows computers and servers to communicate with each other.
In DevOps, networking is essential because applications, servers, and users
must connect reliably.

If networking fails, services become unreachable.

---

## IP Address
An IP address uniquely identifies a computer or server on a network.
It is similar to a house address.

Example:
```
192.168.1.10
```
Command used to view IP address:
```
ip a
```
## What is a Port?
A port is a logical endpoint that allows multiple services to run on the same
server using different numbers.
- IP address = computer
- Port = door to a specific service

Common ports:
- 22 – SSH
- 80 – HTTP
- 443 – HTTPS
## Services and Ports
Services listen on specific ports to accept network connections.

Examples:
- SSH service listens on port 22
- Web servers listen on ports 80 or 443

Command used to view listening ports:
```
ss -tuln
```
## Why “Connection Refused” Happens
The “connection refused” error usually occurs when:
- The service is not running
- The service is not listening on the expected port
- A firewall is blocking the connection
This is a common issue in server and DevOps environments.

## Practical Commands Used
```
ip a
ss -tuln
ping google.com
curl google.com
```
## Why Networking Matters in DevOps
Networking knowledge helps DevOps engineers:
- Diagnose connection issues
- Ensure services are accessible
- Manage cloud servers and applications
- Troubleshoot production problems

  
