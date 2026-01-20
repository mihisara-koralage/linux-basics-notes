# Day 35 – Dockerfile
## What is Dockerfile?
A Dockerfile is a recipe

It tells Docker:

“How to build my image step by step”

Instead of manually installing things every time, you automate it.
## Difference: image vs container
- image     - Blueprint of the system
- container - Running instance of image 
## Meaning of FROM, RUN, COPY, CMD
### Basic Dockerfile Structure
```Dockerfile
FROM ubuntu:22.04
RUN apt update && apt install -y nginx
COPY index.html /var/www/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
- FROM   - Base image, Every image starts from another image
- RUN    - Runs commands at build time, Used to install packages
- COPY   - Copy files from host → container
- EXPOSE - Documents which port the app uses
- CMD    - Command that runs when container starts
## Command: docker build
```bash
docker build -t my-nginx:v1 .
```
