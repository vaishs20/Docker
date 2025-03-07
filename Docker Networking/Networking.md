# Docker Networking

Docker networking enables communication between containers and with the outside world. Understanding networking is crucial for building multi-container applications.

## Default Docker Networks

Docker comes with three built-in network drivers that provide different levels of networking functionality:

### Bridge Network (`bridge`)

- **Default network** for containers if you don't specify a network
- Creates an internal private network on the host
- Containers on the same bridge network can communicate with each other
- Requires port mapping to be accessible from outside

```bash
# Run a container on the default bridge network
docker run -d nginx

# Inspect the default bridge network
docker network inspect bridge
```

### Host Network (`host`)

- Removes network isolation between container and host
- Container uses the host's networking directly
- No need for port mapping; uses host's ports directly
- Potentially better performance but less secure

```bash
# Run a container using host networking
docker run --network=host -d nginx

# Container will be accessible on host's port 80 directly
```

### None Network (`none`)

- Disables all networking for the container
- Container has only a loopback interface
- Useful for running isolated processes
- Most restrictive network option

```bash
# Run a container with no networking
docker run --network=none -d nginx
```

## Creating Custom Networks

Custom networks allow better isolation and communication between related containers.

```bash
# Create a custom bridge network
docker network create my-network

# Create a network with custom subnet and gateway
docker network create --subnet=192.168.0.0/24 --gateway=192.168.0.1 my-custom-net

# Create an overlay network (for Docker Swarm)
docker network create --driver=overlay swarm-network
```

## Connecting Containers to Networks

Containers can be connected to networks at creation time or afterward.

```bash
# Connect at creation time
docker run --network=my-network --name web -d nginx

# Connect an existing container
docker network connect my-network container_id

# Disconnect a container
docker network disconnect my-network container_id

# Run on multiple networks
docker run --network=network1 --network=network2 -d nginx
```

## Exposing Container Ports

To communicate with containers from outside the Docker host, you need to expose ports.

```bash
# Map container port 80 to host port 8080
docker run -p 8080:80 -d nginx

# Map container port 80 to a random host port
docker run -P -d nginx

# Bind to specific host IP address
docker run -p 192.168.1.100:8080:80 -d nginx

# Map UDP ports
docker run -p 53:53/udp -d dns-server

# Map multiple ports
docker run -p 80:80 -p 443:443 -d nginx
```

## Communicating Between Containers

### Using Network Aliases

Network aliases provide DNS resolution between containers in the same network.

```bash
# Create containers with network aliases
docker run --network=my-network --name web --network-alias=webapp -d nginx
docker run --network=my-network --name db --network-alias=database -d mysql

# Now 'web' container can connect to the 'db' container using the hostname 'database'
```

### Container Name Resolution

On custom networks, containers can refer to each other by container name.

```bash
# Create containers on the same network
docker run --network=my-network --name web -d nginx
docker run --network=my-network --name db -d mysql

# Now 'web' container can connect to the 'db' container using the hostname 'db'
```

## Advanced Networking Techniques

### Network Inspection and Troubleshooting

```bash
# List all networks
docker network ls

# Inspect network details
docker network inspect my-network

# See which containers are connected to a network
docker network inspect my-network -f '{{range .Containers}}{{.Name}} {{end}}'

# View container's network settings
docker inspect --format='{{json .NetworkSettings.Networks}}' container_id
```

### Container IP Address Management

```bash
# Assign static IP to a container (on a custom network)
docker run --network=my-network --ip=192.168.0.100 -d nginx

# Get container's IP address
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_id
```

### MacVLAN and IPVLAN Networks

For giving containers their own MAC addresses and direct access to the physical network:

```bash
# Create a macvlan network
docker network create -d macvlan \
  --subnet=192.168.0.0/24 \
  --gateway=192.168.0.1 \
  -o parent=eth0 macvlan-net

# Run a container on the macvlan network
docker run --network=macvlan-net -d nginx
```

## Working with Docker Compose Networks

Docker Compose simplifies networking for multi-container applications.

Example `docker-compose.yml` with custom networking:

```yaml
version: '3'

services:
  web:
    image: nginx
    networks:
      - frontend

  app:
    image: my-app
    networks:
      - frontend
      - backend

  db:
    image: mysql
    networks:
      - backend

networks:
  frontend:
    driver: bridge
  backend:
    driver: bridge
    internal: true  # No internet access, only container-to-container
```

## Network Security Best Practices

1. **Use custom networks** to isolate groups of containers
2. **Implement the principle of least privilege** - only expose necessary ports
3. **Use internal networks** for databases and backend services
4. **Regularly audit network configurations**
5. **Consider using Docker network policies** with Docker Enterprise/Swarm
