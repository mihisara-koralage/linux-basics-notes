# Day 41 – Docker Best Practices & Image Optimization
## Base image choice
Use Official & Small Base Images:
```dockerfile
FROM ubuntu:22.04
FROM nginx:alpine
```
Smaller image = faster builds + safer.
## Layer optimization
Each Dockerfile instruction creates a layer.
```dockerfile
RUN apt update
RUN apt install -y nginx
```
Creates two layers.

Combine:
```dockerfile
RUN apt update && apt install -y nginx
```
Fewer layers = smaller image.
## Cache cleanup
```dockerfile
RUN apt update \
 && apt install -y nginx \
 && rm -rf /var/lib/apt/lists/*
```
## Security mindset
Don’t Run Everything as root.
```dockerfile
RUN useradd -m appuser
USER appuser
```
Not always required, but good practice.
## .dockerignore
Create ```.dockerignore:```
```bash
node_modules
.git
.env
```
- Prevents copying junk into image
- Faster builds
- More secure
## Tagging
```bash
docker build -t myapp:v1 .
docker build -t myapp:1.0.0 .
```
