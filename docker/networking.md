# Docker - Networking

> Learn how Docker containers communicate with each other, the host machine, and the outside world.

<br>

# 🧠 Main Idea

Docker Networking enables communication between containers, the host machine, and external networks.

By default, containers are isolated. Docker networks allow them to exchange data securely and efficiently.

<br>

# 🤔 Why Do We Need It?

Without networking:

- Containers cannot communicate with each other.
- Applications cannot be accessed from outside the container.
- Multi-container applications would not work.

Networking makes it possible to build applications where services like web servers, databases, and caches communicate seamlessly.

<br>

# 📦 Concept

### What is a Docker Network?

A Docker network is a virtual network that connects containers.

Docker automatically creates networks and connects containers when needed.

<br>

### How Containers Communicate

```text
Container A
      │
      │
      ▼
Docker Network
      ▲
      │
      │
Container B
```

Containers connected to the same network can communicate directly.

<br>

### Host and Container

```text
Host Machine
      │
      │ Port Mapping
      ▼
Container
```

Applications inside containers are **not accessible** from the host unless a port is published.

Example:
```bash
docker run -p 8080:80 nginx
```

- `8080` → Host Port
- `80` → Container Port

Now the application is available at:
```text
http://localhost:8080
```

<br>

### Custom Bridge Network

A user-created bridge network.

Advantages:
- Automatic DNS resolution
- Better isolation
- Easier communication between related containers

Example:
```bash
docker network create my-network
```

Run containers on the network:
```bash
docker run --network my-network nginx
```

<br>

## DNS Resolution

Containers on the same custom network can communicate using **container names** instead of IP addresses.

Example:
```text
Web Container
      │
      ▼
Database Container
```

Instead of:
```text
172.18.0.2
```

Docker automatically resolves the name.

<br>

### Inspect Networks

Show available networks:
```bash
docker network ls
```

Inspect a network:
```bash
docker network inspect bridge
```

Remove a network:
```bash
docker network rm my-network
```

<br>

# 🔍 Examples

Run Nginx and expose port 80:
```bash
docker run -d -p 8080:80 nginx
```

Create a custom network:
```bash
docker network create app-network
```

Run two containers on the same network:
```bash
docker run -d --name web --network app-network nginx

docker run -d --name database --network app-network postgres
```

List networks:
```bash
docker network ls
```

Inspect a network:
```bash
docker network inspect app-network
```

<br>

# ⚠️ Common Problems

### Forgetting Port Mapping

Without publishing a port, the application cannot be accessed from the host.

<br>

### Containers Cannot Reach Each Other

Containers must be connected to the same network.

Using a custom bridge network is usually the best solution.

<br>

### Using IP Addresses

Container IP addresses can change.

Use container names instead.

<br>

### Assuming Every Container Is Public

Containers are private by default.

Only published ports are accessible from outside.

<br>

# 💡 Keep in Mind

- Containers are isolated by default.
- A Docker network allows containers to communicate.
- `bridge` is the default network driver.
- `-p HOST:CONTAINER` publishes a container port.
- Custom bridge networks provide automatic DNS resolution.
- Use container names instead of IP addresses whenever possible.
- Host networking removes network isolation.
- `docker network ls` shows available networks.
- `dockernetwork inspect` displays detailed network information.
