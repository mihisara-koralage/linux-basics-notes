# Day 19: System Automation & Environment Setup
## What is system automation
Instead of manually doing:
- apt update
- apt install
- Create folders
- Set permissions

DevOps writes one script that:
- Prepares the system
- Can be run again and again safely

This is how:
- Cloud servers are initialized
- CI/CD runners are configured

## Setup script example
```
#!/bin/bash
set -e

echo "Updating system..."
sudo apt update -y

echo "Installing tools..."
sudo apt install -y git curl nginx

echo "Creating app directory..."
mkdir -p /opt/myapp

echo "Setup completed successfully!"
```
## What idempotency means
Idempotent script:
- Can be run multiple times
- Doesn’t break the system
- Doesn’t duplicate work

Examples:
mkdir -p 
apt install -y 

## Why automation matters in DevOps
This same idea is used in:
- Cloud-init scripts
- Dockerfiles
- Ansible playbooks
- CI/CD pipeline setup steps
