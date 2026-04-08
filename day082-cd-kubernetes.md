# Day 082 – CI/CD Kubernetes Deploy

## Objective

Auto deploy app to Kubernetes from CI.

## Pipeline

Git push  
↓  
Build Docker image  
↓  
Push to Docker Hub  
↓  
Deploy to Kubernetes  

## Commands

kubectl apply -f deployment.yaml  
kubectl apply -f service.yaml  

## CI Deploy

kubectl set image deployment/myapp myapp=image

## Key Learning

CI can automatically deploy to Kubernetes cluster.
