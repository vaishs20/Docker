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

