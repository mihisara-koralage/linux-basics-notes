# Day 26 – Docker Container Lifecycle & Cleanup
## Container lifecycle diagram
A container goes through these states:
```
Created → Running → Stopped → Removed
```

Important:
- Containers do not run forever unless designed to
- Stopped containers still consume disk space
## Commands with explanations
### List Containers
Running containers:
```
sudo docker ps
```
All containers:
```
sudo docker ps -a
```
### Run Container with Name
```
sudo docker run --name test-container my-first-image
```
### Stop & Start Container
```
sudo docker stop test-container
sudo docker start test-container
```
### Restart Container
```
sudo docker restart test-container
```
### Remove Containers
Remove stopped container:
```
sudo docker rm test-container
```
Force remove running container:
```
sudo docker rm -f test-container
```
### Cleanup Unused Containers
```
sudo docker container prune
```
### Remove Images
```
sudo docker rmi my-first-image
sudo docker rmi -f my-first-image
```
### Full Docker Cleanup
```
sudo docker system prune
```
## Why prune is dangerous in prod
This removes:
- Stopped containers
- Unused images
- Unused networks
