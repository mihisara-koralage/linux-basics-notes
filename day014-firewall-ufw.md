# Day 14: Firewalls & UFW
## What Is a Firewall?
A firewall is like a security guard for your server.
- Allows trusted traffic
- Blocks unwanted traffic
Even if a service is running: Firewall can block access
## Why Firewalls Are Critical in DevOps
Cloud servers are exposed to the internet.
Without a firewall:
- Anyone can try to access your server
- Security risks increase
DevOps engineers:
- Open only required ports
- Block everything else
## What is UFW?
UFW (Uncomplicated Firewall) is a simple firewall tool for Ubuntu.
```
sudo ufw status : Check status
sudo ufw enable : Enable firewall
```
- Always allow SSH before enabling on real servers.
## Allow and Block Ports
```
sudo ufw allow ssh : Allow SSH
sudo ufw allow 80  : Allow a specific port
sudo ufw deny 8080 : Block a port
```
## View Rules
```
sudo ufw status numbered
sudo ufw delete 1 : Delete a rule
```
## What I practice
```
sudo ufw status
sudo ufw allow 80
sudo ufw status
```



