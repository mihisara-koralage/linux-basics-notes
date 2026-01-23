# Day 39 – Docker Networking
## Why localhost doesn’t work between containers
```localhost``` inside a container ≠ your computer
- Inside a container:
  - ```localhost``` = that container itself
- It does NOT mean:
  - Host machine
  - Another container
## What is a Docker Network?
A Docker network:
- Is a virtual network
- Created automatically by Docker
- Allows containers to communicate securely

Docker gives each container:
- Its own IP
- Its own hostname
## Service-name-based communication
When you use Docker Compose:
- Docker creates a default bridge network
- All services are connected to it
- Services can talk using service names

Docker:
- Creates internal DNS
- Resolves service names → container IPs
- Updates automatically if containers restart
## Compose networking explanation
Example:
```yaml
services:
  web:
    image: myapp
  db:
    image: mysql
```
```web``` can connect to database at:
```makefile
db:3306
```
