# Day 24 — Containers & Docker
## What is a container?
A lightweight, isolated environment to run an application with everything it needs.

Includes:
- App code
- Runtime (Python / Java / Node)
- Libraries
- Dependencies

Runs on the same OS kernel → very fast.
## Containers vs VMs
| Virtual Machine | Container         |
| --------------- | ----------------- |
| Heavy           | Lightweight       |
| Has full OS     | Shares host OS    |
| Slow start      | Starts in seconds |
| More RAM        | Less RAM          |

## What is Docker
Docker is a tool to:
- Build containers
- Run containers
-Manage containers

Think of Docker as:

“Git for applications + environments”
## Docker terms
- Image → Blueprint (read-only)
- Container → Running instance of an image
- Dockerfile → Instructions to build an image
- Docker Hub → Image store (like GitHub)
## Commands you learned
```
docker run hello-world
docker run -d -p 8080:80 nginx
```
Explanation:
- -d → detached (background)
- -p 8080:80 → port mapping
- nginx → web server
```
http://localhost:8080
```
