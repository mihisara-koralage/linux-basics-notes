# Day 30 – Docker Compose
## Why Docker Compose?
Without Compose:
```bash
docker run app
docker run db
docker run redis
```
Problems:
- Hard to manage
- Many commands
- No structure

Docker Compose solves this
- One file → One command → Entire app stack
## Structure of YAML
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
## Commands used
```bash
docker compose up -d
docker ps
curl localhost:8080
docker compose down
```
## Real-World DevOps Usage
Docker Compose is used for:
- Local development
- Testing environments
- CI pipelines
- Microservices simulation
