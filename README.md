# Docker
Here’s a comprehensive **Docker syllabus** tailored for SREs, DevOps engineers, and developers. This syllabus is structured to take you from **beginner to advanced** level, covering both theoretical concepts and hands-on practical exercises.

---

### **Docker Syllabus**

#### **1. Introduction to Docker**
   - What is Docker?
   - Why use Docker?
   - Docker vs Virtual Machines
   - Docker architecture (Docker Engine, Docker Daemon, Docker Client)
   - Key concepts: Images, Containers, Registries

#### **2. Installing Docker**
   - Installing Docker on Linux, macOS, and Windows
   - Verifying the installation (`docker --version`, `docker info`)
   - Configuring Docker to start on boot

#### **3. Working with Docker Images**
   - Pulling images from Docker Hub (`docker pull`)
   - Listing images (`docker images`)
   - Removing images (`docker rmi`)
   - Searching for images (`docker search`)
   - Building custom images using Dockerfile (`docker build`)
   - Tagging images (`docker tag`)

#### **4. Working with Docker Containers**
   - Running containers (`docker run`)
   - Listing running containers (`docker ps`)
   - Stopping and removing containers (`docker stop`, `docker rm`)
   - Running containers in detached mode (`-d`)
   - Executing commands in a running container (`docker exec`)
   - Viewing container logs (`docker logs`)
   - Inspecting containers (`docker inspect`)
   - Copying files between host and container (`docker cp`)

#### **5. Dockerfile Basics**
   - Understanding Dockerfile syntax
   - Common instructions:
     - `FROM`, `RUN`, `COPY`, `ADD`, `CMD`, `ENTRYPOINT`, `ENV`, `WORKDIR`, `EXPOSE`, `VOLUME`
   - Best practices for writing Dockerfiles
   - Multi-stage builds

#### **6. Docker Networking**
   - Default Docker networks (`bridge`, `host`, `none`)
   - Creating custom networks (`docker network create`)
   - Connecting containers to networks
   - Exposing container ports (`-p` flag)
   - Communicating between containers using network aliases

#### **7. Docker Volumes and Storage**
   - Understanding Docker volumes
   - Creating and managing volumes (`docker volume create`, `docker volume ls`)
   - Mounting volumes in containers (`-v` flag)
   - Using bind mounts
   - Persistent data storage with volumes

#### **8. Docker Compose**
   - What is Docker Compose?
   - Writing `docker-compose.yml` files
   - Starting and stopping multi-container applications (`docker-compose up`, `docker-compose down`)
   - Scaling services (`docker-compose scale`)
   - Environment variables in Compose
   - Networking in Docker Compose

#### **9. Docker Registry**
   - Introduction to Docker Hub
   - Pushing and pulling images to/from Docker Hub (`docker push`, `docker pull`)
   - Setting up a private Docker registry
   - Managing access to private registries

#### **10. Docker Security**
   - Best practices for securing Docker containers
   - Running containers as non-root users
   - Limiting container resources (CPU, memory)
   - Scanning images for vulnerabilities (`docker scan`)
   - Using Docker Content Trust (DCT) for image signing

#### **11. Docker in CI/CD Pipelines**
   - Integrating Docker with Jenkins, GitLab CI, or GitHub Actions
   - Building and pushing Docker images in CI/CD pipelines
   - Running tests in Docker containers
   - Automating deployments using Docker

#### **12. Advanced Docker Concepts**
   - Docker Swarm (orchestration and clustering)
   - Docker overlay networks
   - Docker secrets management
   - Docker health checks
   - Docker logging drivers
   - Docker plugins

#### **13. Kubernetes and Docker**
   - Understanding the role of Docker in Kubernetes
   - Running Docker containers in Kubernetes pods
   - Migrating from Docker Swarm to Kubernetes (optional)

#### **14. Monitoring and Troubleshooting Docker**
   - Monitoring Docker containers using `docker stats`
   - Using `cAdvisor` and `Prometheus` for container monitoring
   - Troubleshooting common Docker issues (e.g., container crashes, network issues)

---

### **Hands-On Exercises**

#### **Beginner**
1. Run a simple `nginx` container and access it via a browser.
2. Create a custom Dockerfile for a Python Flask app and build an image.
3. Use Docker volumes to persist data for a MySQL container.

#### **Intermediate**
4. Write a `docker-compose.yml` file to set up a WordPress site with MySQL.
5. Set up a private Docker registry and push/pull images to/from it.
6. Use Docker networking to connect two containers (e.g., a web app and a database).

#### **Advanced**
7. Create a multi-stage Dockerfile for a Java application.
8. Set up Docker Swarm and deploy a multi-service application.
9. Integrate Docker with a CI/CD pipeline (e.g., Jenkins or GitLab CI).

---

### **Tools and Integrations**
- **Docker CLI**: Master the command-line interface.
- **Docker Compose**: For managing multi-container applications.
- **Docker Hub**: For public and private image repositories.
- **Kubernetes**: For container orchestration (optional but recommended).
- **CI/CD Tools**: Jenkins, GitLab CI, GitHub Actions.
- **Monitoring Tools**: Prometheus, Grafana, cAdvisor.

---

### **Learning Resources**
- **Official Docker Documentation**: [https://docs.docker.com](https://docs.docker.com)
- **Docker Hub**: [https://hub.docker.com](https://hub.docker.com)
- **Books**:
  - "Docker Deep Dive" by Nigel Poulton
  - "The Docker Book" by James Turnbull
- **Online Courses**:
  - Docker Mastery on Udemy
  - Docker for Beginners on Pluralsight

---

### **Why This Syllabus?**
- **Beginner-Friendly**: Starts with the basics and gradually moves to advanced topics.
- **Hands-On Focus**: Includes practical exercises to reinforce learning.
- **Real-World Relevance**: Covers topics essential for SREs and DevOps engineers.
