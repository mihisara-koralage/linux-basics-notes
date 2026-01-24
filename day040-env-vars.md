# Day 40 – Docker Environment Variables
## Why env vars are needed
When hardcoding configs we have Problems like:
- Security risk
- Must rebuild image to change config
- Same image can’t be used for dev/prod
Environment variables:
- Store configuration values
- Are injected at runtime
- Keep images clean & reusable
## Docker -e example
```bash
docker run -e APP_ENV=dev nginx
```
Inside container:
```bash
echo $APP_ENV
```
## Compose environment vs .env
```bash
nano .env
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=appdb
```
Use it in Compose:
```bash
version: "3.8"

services:
  db:
    image: mysql:8
    env_file:
      - .env
```
## Secrets mindset
In real DevOps:
- ```.env``` files → not committed to Git
- Secrets stored in:
  - GitHub Secrets
  - AWS Secrets Manager
  - Vault
  - Kubernetes Secrets
