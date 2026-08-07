# Docker - Compose

> Define and manage multi-container applications using a single configuration file.

<br>

# 🧠 Main Idea

Docker Compose is a tool for defining and running **multi-container Docker applications**.

Instead of running multiple `docker run` commands manually, you describe your application's services, networks, and volumes inside a `compose.yaml` file.

Docker Compose then creates and manages all required containers together.

<br>

# 🤔 Why Do We Need It?

Real-world applications usually contain multiple services.

For example:

```text
Application
    |
    ├── Backend API
    |
    ├── Database
    |
    └── Cache
```

Managing each container separately can become difficult.

Docker Compose helps by:

- Managing multiple containers together.
- Keeping configuration in one file.
- Creating networks automatically.
- Managing volumes easily.
- Starting and stopping the whole application with simple commands.

<br>

# 📦 Concept

### What is Docker Compose?

Docker Compose uses a YAML configuration file to describe an application.

The standard file name is:

```text
compose.yaml
```

or:

```text
compose.yml
```

Inside this file, you define:

- Services
- Images
- Containers
- Networks
- Volumes
- Environment variables

<br>

### Services

A service represents a container that is part of your application.

Example:

```yaml
services:
  web:
    image: nginx

  database:
    image: postgres
```

In this example:

- `web` is one service.
- `database` is another service.

Docker Compose creates containers from these services.

<br>

### Compose Workflow

```text
compose.yaml
       │
       ▼
docker compose up
       │
       ▼
Create Networks
       │
       ▼
Create Containers
       │
       ▼
Start Application
```

<br>

### Example compose.yaml

```yaml
services:
  app:
    image: my-app
    ports:
      - "8080:8080"

  database:
    image: postgres
    environment:
      POSTGRES_PASSWORD: password
```

This creates:

- An application container.
- A PostgreSQL database container.
- Network communication between them.

<br>

### Networks in Compose

Docker Compose automatically creates a network for services.

Services can communicate using their service names.

Example:

```text
app
 |
 |
database
```

The application can connect to the database using:

```text
database
```

instead of an IP address.

<br>

### Volumes in Compose

Volumes allow data persistence.

Example:

```yaml
services:
  database:
    image: postgres
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

Database data remains even if the container is removed.

<br>

# 🔍 Examples

Start all services:

```bash
docker compose up
```

Run in background:

```bash
docker compose up -d
```

Stop services:

```bash
docker compose down
```

List running services:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs
```

Build images:

```bash
docker compose build
```

<br>

# ⚠️  Common Problems

### Confusing Compose with Dockerfile

Dockerfile builds an image.

Docker Compose manages multiple containers.

<br>

### Using the Old Command

Older versions used:

```bash
docker-compose up
```

Modern Docker uses:

```bash
docker compose up
```

<br>

### Forgetting Volumes

Without volumes, important data may disappear when containers are removed.

<br>

### Hardcoding Container IP Addresses

Use service names instead.

Docker Compose provides automatic DNS resolution.

<br>

# 💡 Keep in Mind

- Docker Compose manages multi-container applications.
- The main configuration file is `compose.yaml`.
- Services represent containers in an application.
- Compose automatically creates networks.
- Volumes are used for persistent data.
- `docker compose up` starts the application.
- `docker compose down` stops and removes resources.
- Dockerfile builds images; Docker Compose manages services.
- Modern syntax is `docker compose`, not `docker-compose`.
