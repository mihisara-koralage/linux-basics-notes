# Day 34 – Docker Images & Containers
## Image vs Container explanation
- Image → blueprint / template (read-only)
- Container → running instance of an image

 One image ➜ many containers

Example:
- Image: ```nginx```
- Containers: ```nginx-1```, ```nginx-2```, ```nginx-test```
## Commands you ran
~~~bash
docker pull hello-world # Downloads the image from Docker Hub
docker images           # Check images
docker run hello-world  # Run your container
docker ps               # List Running containers only
docker ps -a            # List all containers
~~~
## Nginx port mapping example
~~~bash
docker run -d -p 8080:80 nginx
~~~
Explain:
- -d → detached (runs in background)
- -p 8080:80 → map:
  - host port 8080
  - container port 80
- nginx → image name
## Key learning points
```bash
docker images        # list images
docker ps            # running containers
docker ps -a         # all containers
docker logs <id>     # container logs
docker rm <id>       # remove container
docker rmi <image>   # remove image
```
- Containers are immutable
- If something breaks → delete and recreate
- No manual fixing inside containers
