---
layout: single
title:  DevOps Section - Docker
date:   2025-01-28 12:35:00 +0100
published: true
---

# Docker

Understanding Docker: From Basics to Advanced Concepts

In this comprehensive guide, we'll explore Docker from its fundamental concepts to advanced features, including container orchestration and best practices.

1. Docker Overview

Docker is a platform that enables developers to package applications and their dependencies into lightweight, portable containers. These containers can run consistently across different environments, making it easier to develop, ship, and run applications.

Key concepts:

- Container: A standalone, executable package that includes everything needed to run an application
- Image: A template used to create containers
- Registry: A repository for storing and sharing Docker images
- Dockerfile: A script containing instructions to build a Docker image

2. Essential Docker Commands

Container Management:

docker ps                  # List running containers
docker ps -a              # List all containers
docker start <container>  # Start a container
docker stop <container>   # Stop a container
docker rm <container>     # Remove a container


Image Management:

docker images             # List available images
docker pull <image>       # Download an image
docker rmi <image>        # Remove an image


3. Docker Run Commands

Basic Run Commands:

docker run nginx                  # Run a container
docker run -d nginx              # Run in detached mode
docker run --name web-server nginx  # Run with a specific name


Port Mapping and Volume Mounting:

docker run -p 80:80 nginx        # Map host port to container port
docker run -v /host/path:/container/path nginx  # Mount volume


4. Advanced Docker Run Features

Resource Management:

docker run --memory="512m" nginx      # Memory limit
docker run --cpus="2" nginx          # CPU limit
docker run -e DB_HOST=mysql nginx     # Environment variables
docker run --network=my-network nginx # Network configuration
```

5. Docker Images

Creating Images:

FROM ubuntu:20.04
WORKDIR /app
COPY . .
RUN apt-get update && apt-get install -y python3
ENV PORT=8080
EXPOSE 8080
CMD ["python3", "app.py"]


Environment Variables:
- Set using ENV in Dockerfile
- Override using -e flag during run
- Use environment files with --env-file

CMD vs ENTRYPOINT:
- CMD: Default command, can be overridden
- ENTRYPOINT: Fixed command, parameters can be appended

## 6. Docker Compose

Basic compose file:

version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: example


7. Docker Engine

Components:
- Docker daemon (dockerd)
- REST API
- Docker CLI client
- Manages images, containers, networks, and volumes

8. Docker Storage

Storage Types:
- Volumes: Managed by Docker
- Bind mounts: Direct host filesystem mapping
- tmpfs mounts: Memory-only storage

Volume Commands:

docker volume create my-vol
docker run -v my-vol:/app nginx


9. Docker Networking

Network Commands:

docker network create my-network
docker network ls
docker network connect my-network container1


Network Types:
- bridge: Default network for containers
- host: Container uses host's network
- none: No network access
- overlay: Multi-host networking

10. Docker Registry

Registry Information:
- Docker Hub: https://hub.docker.com
- Private registry format: registry.example.com/username/repository

Registry Commands:

docker login
docker push username/image
docker pull username/image


11. Container Orchestration

Docker Swarm Commands:

docker swarm init                # Initialize Swarm
docker swarm join --token <token>  # Join as worker
docker service create --replicas=3 -p 8080:80 web-server  # Create service


Orchestration Tools:

1. Docker Swarm
   - Native Docker solution
   - Easier to set up
   - Integrated with Docker CLI

2. Kubernetes
   - More powerful and flexible
   - Industry standard
   - Larger ecosystem
   - Can use Docker, Rocket, or CRI-O as runtime

3. Apache Mesos
   - Good for very large scale
   - Complex setup
   - Used by large enterprises

Best Practices:
- Use service replicas for high availability
- Implement proper networking
- Monitor container health
- Use secrets management
- Implement rolling updates



