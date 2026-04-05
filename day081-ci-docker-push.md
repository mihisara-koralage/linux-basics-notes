# Day 081 – CI Push Docker Image

## 🎯 Objective
Push Docker image to Docker Hub using CI.

## Pipeline

git push  
↓  
CI runs  
↓  
Build Docker image  
↓  
Push to Docker Hub  

## Secrets Used

DOCKER_USERNAME  
DOCKER_PASSWORD  

## Image

dockerhubusername/myapp:latest

## Key Learning

CI can automatically build and push images.
