# Day 38 – Docker Compose
## Why Docker Compose is needed
Real applications usually have:
- Web app
- Database
- Cache
- Background workers

With Compose : everything starts together.
## Basic YAML structure
```yaml
version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: root
```
## Commands: up, up -d, down
```bash
docker compose up       # Start services
docker compose up -d    # Background mode
docker compose ps       # Check running containers
docker compose down     # Stop everything
```
## Important DevOps Concepts Learned
- One file = whole app
- Services communicate on same network
- Easy start/stop
- Repeatable deployments
