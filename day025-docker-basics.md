# Day 25 – Docker Basics
## What is Docker
Docker lets you:
- Package your app + dependencies + OS config
- Run it anywhere the same way

Think of Docker as:

“A lightweight virtual machine, but faster”
## Image vs container
- Image     -	Blueprint of your app
- Container -	Running instance of image
## Dockerfile explanation
- Instructions to build image
## Commands you used
Install Docker:
```
sudo apt update
sudo apt install docker.io -y
```
Start Docker:
```
sudo service docker start
docker ps
```
Create a simple app:
```
nano app.sh
#!/bin/bash
echo "Hello from Docker container!"
chmod +x app.sh
```
Create Dockerfile:
```
nano Dockerfile

FROM ubuntu:22.04
WORKDIR /app
COPY app.sh .
RUN chmod +x app.sh
CMD ["./app.sh"]
```
Build Docker Image:
```
sudo docker build -t my-first-image .
sudo docker run my-first-image
```
Check Containers:
```
sudo docker ps -a
```
## Output
```
Hello from Docker container!
```
