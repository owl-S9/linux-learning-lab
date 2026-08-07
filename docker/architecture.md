# Docker - Architecture

> Understand how Docker works internally and how its core components interact with each other.

<br>

# 🧠 Main Idea

Docker is a platform for building, shipping, and running applications inside lightweight, isolated environments called **containers**.

Instead of running applications directly on the host operating system, Docker packages everything an application needs into an **image** and runs it as a **container**.

Docker follows a **client-server architecture**, where different components work together to build, manage, and run containers.

<br>

# 🤔 Why Do We Need It?

Understanding Docker architecture helps you:

- Understand what happens behind every Docker command.
- Troubleshoot Docker problems more easily.
- Learn Docker commands much faster.
- Build a strong foundation for Docker Compose, Kubernetes, and DevOps.
- Understand the relationship between Images, Containers, Networks, and Volumes.

<br>

# 📦 Concept

## Architecture Overview

```text
                +------------------+
                |  Docker Client   |
                | docker commands  |
                +---------+--------+
                          |
                          | REST API
                          |
                +---------v--------+
                | Docker Daemon    |
                |    (dockerd)     |
                +----+--------+----+
                     |        |
          manages    |        | manages
                     |        |
           +---------v-+   +--v----------+
           |  Images   |   | Containers  |
           +-----------+   +-------------+
                     |
                     |
             Pull / Push Images
                     |
             +-------v-------+
             | Docker Hub    |
             | or Registry   |
             +---------------+
```

<br>

### Docker Client

The Docker Client is the command-line interface (CLI) that users interact with.

Examples:

```bash
docker run
docker build
docker ps
docker pull
```

The client **does not** run containers itself.

It simply sends requests to the Docker Daemon.

<br>

### Docker Daemon (dockerd)

The Docker Daemon is the background service that performs all Docker operations.

Responsibilities:

- Build images
- Run containers
- Manage networks
- Manage volumes
- Pull images
- Remove containers

Every Docker command eventually reaches the Docker Daemon.

<br>

### Docker Engine

Docker Engine is the complete runtime that powers Docker.

It consists of:

- Docker Client
- Docker Daemon
- Docker API

When people say **"Install Docker"**, they usually mean installing Docker Engine.

<br>

### Docker Images

An **Image** is a read-only template used to create containers.

Images contain:

- Application code
- Runtime
- Libraries
- Dependencies
- Configuration

One image can create many containers.

<br>

### Docker Containers

A **Container** is a running instance of an image.

Containers are:

- Lightweight
- Isolated
- Fast
- Portable

Stopping or deleting a container does not remove its image.

<br>

### Docker Registry

A Registry stores Docker images.

The most popular registry is **Docker Hub**.

Common operations:

- Pull images
- Push images
- Share images

Docker also supports private registries.

<br>

### Docker Volumes

Volumes store persistent data outside containers.

Without a volume, deleting a container usually deletes its data.

Volumes allow data to survive container removal.

<br>

### Docker Networks

Networks allow containers to communicate with:

- Other containers
- The host machine
- External systems

<br>

### Docker API

The Docker API allows applications and tools to communicate directly with the Docker Daemon.

The Docker CLI uses this API internally.

<br>

### Dockerfile

A **Dockerfile** is a text file containing instructions for building a Docker image.
It defines everything needed for the image, such as:
Docker reads the Dockerfile and builds an image from it.

<br>

### Docker Compose

Docker Compose is a tool for defining and managing **multi-container applications**.
Instead of running multiple `docker run` commands manually, you describe all services in a single `compose.yaml` file.
Docker Compose can start, stop, and manage all related containers with a single command.

<br>

# ⚠️  Common Problems

### Confusing Images and Containers

An Image is a template.

A Container is a running instance of that template.

<br>

### Thinking Docker Client Runs Containers

The Docker Client only sends commands.

The Docker Daemon performs the actual work.

<br>

### Assuming Containers Store Data Permanently

Container files are temporary.

Use Volumes for persistent storage.

<br>

### Believing Docker Hub Is Required

Docker Hub is only one registry.

Docker also supports private registries.

<br>

# 💡 Keep in Mind

- Docker uses a **client-server architecture**.
- The Docker Client communicates with the Docker Daemon.
- The Docker Daemon performs all Docker operations.
- Images are templates.
- Containers are running instances of images.
- One image can create multiple containers.
- Volumes keep data persistent.
- Networks connect containers.
- Registries store and distribute images.
- Docker Engine includes the Client, Daemon, and API.
