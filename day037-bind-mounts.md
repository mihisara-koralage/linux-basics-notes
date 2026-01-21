# Day 37 – Bind Mounts
## What is a Bind Mount?
- Links a folder on your machine
- Directly into a folder inside the container
## Bind Mount vs volumes
| Feature           | Bind Mount  | Volume     |
| ----------------- | ----------- | ---------- |
| Managed by Docker |  No         |  Yes       |
| Uses local folder |  Yes        |  No        |
| Best for          | Development | Production |
| Risk              | Higher      | Lower      |
| Performance       | Slower      | Faster     |

## Dev vs prod 
### Development:
- Bind mounts
- Local code
- Fast iteration
### Production:
- Docker images
- Volumes
- Stability & security
## Commands I used
```bash
mkdir ~/nginx-bind
cd ~/nginx-bind

# Create HTML file
echo "Hello from Bind Mount" > index.html

# Run container with bind mount
docker run -d \
  --name nginx-bind \
  -p 8081:80 \
  -v $(pwd):/usr/share/nginx/html \ # $(pwd) → current folder on your laptop
  nginx
```
