# Day 36 – Docker Volumes
## What problem volumes solve
By default:
- Containers are temporary
- If a container is deleted → all data inside is lost

A Docker volume is:
- Storage outside the container
- Managed by Docker
- Survives container deletion
## Commands I used
```bash
docker volume create mydata  # Create volume
docker volume ls             # List volumes
```
## Small real-world example (nginx)
### Run container with volume
```bash
docker run -d \
  --name nginx-vol \
  -p 8080:80 \
  -v mydata:/usr/share/nginx/html \
  nginx
```
### Create a file inside container
```bash
docker exec -it nginx-vol bash
echo "Hello from Docker Volume" > /usr/share/nginx/html/index.html
```
- Even if we delete this container and add this volume to new container data is still available there.
- This is persistence.
## Why Volumes Matter in DevOps
- Databases keep data
- Logs survive restarts
- Safe deployments
- Zero data loss during updates
