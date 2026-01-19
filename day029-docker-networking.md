# Day 29 – Docker Networking & Port Mapping
## What is a Port?
A port is a door on your server.

Examples:
- 80 → HTTP
- 443 → HTTPS
- 22 → SSH
- 3306 → MySQL

Apps listen on ports.
## Port mapping syntax
```bash
docker run -d --name web -p 8080:80 nginx
```
## nginx example
```bash
docker run -d --name web -p 8080:80 nginx
curl localhost:8080
```
## Common Mistakes
- Forgetting to expose ports
- Mapping wrong ports
- Opening unnecessary ports (security risk)
- Using random ports in production
