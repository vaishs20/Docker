# Docker Basics Notes

## Dockerfile

### Introduction
A **Dockerfile** contains a set of instructions to build a Docker image. It defines the base image, application source code, dependencies, and any necessary configuration or commands.

### Dockerfile Basics

#### Understanding Dockerfile Syntax
Dockerfile uses simple **instruction** statements, each performing a specific action during the image build process.

#### Common Dockerfile Instructions

| Instruction | Description |
|---|---|
| `FROM` | Specifies the base image to use |
| `COPY` | Copies files from local filesystem into the image |
| `ADD` | Similar to COPY, but can also fetch from URLs and unpack archives |
| `RUN` | Runs commands inside the image (e.g., installing dependencies) |
| `CMD` | Defines the command to run when container starts |
| `ENTRYPOINT` | Similar to CMD, but often used for executables |
| `ENV` | Sets environment variables |
| `WORKDIR` | Sets the working directory inside the image |
| `EXPOSE` | Informs which ports the container will listen on |
| `VOLUME` | Defines mount points for persistent storage |

#### Best Practices for Writing Dockerfiles
- Use a small and efficient base image (e.g., `alpine` when possible)
- Minimize layers by combining commands where feasible
- Clean up temporary files in the same layer to reduce image size
- Use `.dockerignore` to avoid unnecessary files being copied
- Set explicit versions for dependencies to ensure reproducibility

---

## Example Dockerfile
```Dockerfile
# Use official Node.js image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy application source
COPY . .

# Expose application port
EXPOSE 3000

# Start application
CMD ["node", "app.js"]
```

---

## Docker Image

### Introduction
A **Docker image** is the blueprint for a container. It contains:
- Application source code
- All required dependencies
- Configuration

### Pre-built Images
- Images can be built manually using a Dockerfile.
- Pre-built images can also be **pulled** from **Docker Hub** or other registries.

### Image Caching
- Docker caches image layers to speed up builds.
- If **application code changes**, a new image build will update only the changed layers, reusing cache where possible.

---

## Docker Container

### Introduction
A **Docker container** is a running instance of a Docker image. It’s isolated, lightweight, and runs your application consistently across environments.

### Build and Run Container
- Build image from Dockerfile:
```bash
docker build -t myapp:latest .
```
- Run container from image:
```bash
docker run myapp:latest
```
- Run container in background (detached mode), useful for servers like MySQL:
```bash
docker run -d mysql:latest
```

### About `-d` Flag
- `-d` stands for **detached mode**.
- When running in detached mode, the container runs in the background, and you get back the command prompt immediately.
- This is useful for long-running services like databases or web servers.
- Example for running a web server in detached mode:
```bash
docker run -d -p 8080:80 nginx:latest
```
- To check logs from a detached container, use:
```bash
docker logs <container_id>
```
- To stop a detached container, use:
```bash
docker stop <container_id>
```

---

## Docker Hub

### Introduction
**Docker Hub** is the default public and private **image registry**.
- You can pull public images directly.
- You can push your own images (public or private).

### Example Commands
| Command | Description |
|---|---|
| `docker pull` | Pull image from Docker Hub or other registry |
| `docker push` | Push image to Docker Hub (if authenticated) |

---

## Environment Variables and Server Configurations

Some servers (like MySQL) and databases require setting environment variables before starting. Example:
```bash
docker run -d -e MYSQL_ROOT_PASSWORD=secret mysql:latest
```

---

## Summary of Key Commands

| Command | Description |
|---|---|
| `docker build` | Build image from Dockerfile |
| `docker run` | Create container from image |
| `docker ps` | List running containers |
| `docker images` | List available images |
| `docker pull` | Pull image from Docker Hub |
| `docker push` | Push image to Docker Hub |
| `docker rmi` | Remove one or more images |
| `docker search` | Search for images on Docker Hub |
| `docker tag` | Tag an image to create an alias (helpful for pushing to registries) |
| `docker stop` | Stop a running container |
| `docker rm` | Remove a stopped container |
| `docker exec` | Run a command inside a running container (e.g., open a shell) |
| `docker logs` | View logs from a running container |
| `docker inspect` | View detailed information about a container |
| `docker cp` | Copy files between host and container |

---



