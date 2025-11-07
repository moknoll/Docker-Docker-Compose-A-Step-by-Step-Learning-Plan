# Docker & Docker Compose: A Step-by-Step Learning Plan

This document provides a structured plan for learning Docker and Docker Compose, from fundamental concepts to managing multi-container applications.

## Part 1: Docker Fundamentals

### Step 1: Introduction to Docker

*   **What is Docker?** Docker is a platform for developing, shipping, and running applications in containers. Containers are lightweight, portable, and self-sufficient, ensuring that your application works seamlessly in any environment.
*   **Why use Docker?** It solves the "it works on my machine" problem, simplifies dependency management, and enables microservices architectures.
*   **Docker Architecture:**
    *   **Docker Client:** The command-line tool that you interact with.
    *   **Docker Engine (Daemon):** The background service that manages containers.
    *   **Docker Registry:** A place to store and distribute Docker images (like Docker Hub).
*   **Containers vs. Virtual Machines:** Understand the key differences in terms of architecture and resource usage.

### Step 2: Installation and Setup

*   Install **Docker Desktop** for Mac or Windows, or **Docker Engine** for Linux. You can find the official installation guides here: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
*   Verify your installation by running `docker --version` in your terminal.

### Step 3: Core Docker Concepts & Commands

*   **Images and Containers:** An **image** is a blueprint for your application, and a **container** is a running instance of that image.
*   Run your first container: `docker run hello-world`
*   List running containers: `docker ps`
*   List all containers (including stopped ones): `docker ps -a`
*   Manage containers:
    *   `docker start <container_id>`
    *   `docker stop <container_id>`
    *   `docker rm <container_id>`
*   Run a container interactively: `docker run -it ubuntu bash`

### Step 4: Docker Images

*   **What are Docker Images?** Read-only templates that contain the application code, libraries, and dependencies.
*   **Pulling images from Docker Hub:** `docker pull nginx`
*   **Listing images:** `docker images`
*   **Creating images with a Dockerfile:**
    *   A `Dockerfile` is a text file with instructions on how to build a Docker image.
    *   **Key Instructions:**
        *   `FROM`: Specifies the base image.
        *   `RUN`: Executes commands in the image.
        *   `COPY`: Copies files from your local machine to the image.
        *   `CMD`: The default command to run when the container starts.
    *   **Building an image:** `docker build -t my-app:1.0 .`

### Step 5: Data Persistence and Volumes

*   Containers are ephemeral, meaning data is lost when the container is removed.
*   **Volumes** are used to persist data outside the container's lifecycle.
*   Create and mount a volume: `docker run -v my-data:/app/data my-app`
*   Manage volumes:
    *   `docker volume create my-volume`
    *   `docker volume ls`
    *   `docker volume inspect my-volume`

## Part 2: Docker Compose

### Step 6: Introduction to Docker Compose

*   **What is Docker Compose?** A tool for defining and running multi-container Docker applications.
*   It uses a YAML file (`docker-compose.yml`) to configure the application's services.

### Step 7: Writing a `docker-compose.yml` file

*   **Services:** Each container in your application is a service.
*   **Image:** The Docker image for the service.
*   **Ports:** Map ports between the host and the container.
*   **Volumes:** Mount volumes for data persistence.
*   **Networks:** Define networks for communication between services.

### Step 8: Running and Managing Multi-Container Applications

*   Start all services: `docker-compose up`
*   Start in detached mode: `docker-compose up -d`
*   Stop all services: `docker-compose down`
*   View logs for all services: `docker-compose logs`
*   View logs for a specific service: `docker-compose logs -f my-service`

### Step 9: Practical Project: Web App with a Database

Here is a simple example of a `docker-compose.yml` for a Python web application using Flask and a Redis database:

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: "redis:alpine"
```

In this example, you would have a `Dockerfile` in the same directory to build the `web` service.

## Part 3: Advanced Topics & Resources

### Step 10: Further Learning

*   **Docker Networking:** Learn about bridge networks, overlay networks, and how to connect containers.
*   **Docker Hub:** Create your own repositories and push your images.
*   **Security Best Practices:** Learn how to write secure Dockerfiles and manage container security.

### Recommended Resources

*   **Official Docker Documentation:** [https://docs.docker.com/](https://docs.docker.com/)
*   **Docker 101 Tutorial:** [https://www.docker.com/101-tutorial/](https://www.docker.com/101-tutorial/)
*   **GeeksforGeeks Docker Tutorial:** [https://www.geeksforgeeks.org/docker-tutorial/](https://www.geeksforgeeks.org/docker-tutorial/)
*   **DevOps with Docker (University of Helsinki):** [https://devopswithdocker.com/](https://devopswithdocker.com/)
*   **Udemy Courses:**
    *   Docker for the Absolute Beginner - Hands On - DevOps
    *   Docker & Kubernetes: The Practical Guide
