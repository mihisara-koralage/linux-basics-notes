# Day 31 – Environment Variables & Secrets
## What Are Environment Variables?
Environment variables are:
- Key–value pairs
- Used to configure apps without changing code

Apps read them at runtime.
## Why secrets shouldn’t be in code?
Problems:
- Leaks on GitHub
- Shared with team
- Hard to rotate
## .env usage
```bash
nano .env
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=mydb
```
## docker-compose example
```bash
nano docker-compose.yml
```
```yaml
version: "3.8"

services:
  db:
    image: mysql:8
    env_file:
      - .env
```
Docker Compose automatically loads .env.
## Best practices
### Add .gitignore
```bash
nano .gitignore
```
Add:
```
.env
```
### Environment Variables in Containers
```
docker exec -it <container_id> env
```
### Real-World DevOps Practices
| Environment | How secrets handled |
| ----------- | ------------------- |
| Local       | .env                |
| CI/CD       | Secret variables    |
| Cloud       | AWS Secrets Manager |
| Kubernetes  | Secrets             |
