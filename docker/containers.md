# Docker - Containers

> Learn what Docker Containers are, how they work, and how they relate to Docker Images.

<br>

# 🧠 Main Idea

A **Docker Container** is a running instance of a Docker Image.

It is an isolated environment where an application runs with its own filesystem, processes, network, and configuration, while sharing the host operating system's kernel.

Containers are lightweight, fast, and portable.

<br>

# 🤔 Why Do We Need It?

Containers solve the classic **"It works on my machine"** problem.

They provide:

- Isolation
- Portability
- Consistent environments
- Fast startup
- Efficient resource usage
- Easy deployment

Instead of configuring every machine manually, you simply run the same container everywhere.

<br>

# 📦 Concept

### What is a Container?

A container is a **running application** created from an image.

Think of it like this:

```text
Blueprint (Image)
        │
        ▼
Build a House (Container)
```

The image is the blueprint.

The container is the actual running house.

<br>

### Image vs Container

```text
Docker Image
      │
      │ docker run
      ▼
Docker Container
```

- Image = Template
- Container = Running Instance

One image can create multiple containers.

<br>

### Container Lifecycle

```text
Created
   │
   ▼
Running
   │
   ▼
Paused
   │
   ▼
Stopped
   │
   ▼
Removed
```

Common lifecycle commands:

- Create
- Run
- Start
- Stop
- Restart
- Pause
- Unpause
- Remove

<br>

### Container Isolation

Each container has its own:

- Filesystem
- Processes
- Network
- Environment variables

Containers are isolated from each other unless explicitly connected.

<br>

### Writable Layer

Unlike images, containers have a **writable layer**.

Any changes made while the container is running are stored in this layer.

If the container is removed, those changes are usually lost unless a **Volume** is used.

<br>

### Multiple Containers from One Image

```text
           Docker Image
                │
      ┌─────────┼─────────┐
      ▼         ▼         ▼
Container 1 Container 2 Container 3
```

A single image can create any number of independent containers.

<br>

# 🔍 Examples

Run a container:
```bash
docker run nginx
```

Run a container in the background (detached mode):
```bash
docker run -d nginx
```

List running containers:
```bash
docker ps
```

List all containers:
```bash
docker ps -a
```

Stop a container:
```bash
docker stop <container-id>
```

Start a stopped container:
```bash
docker start <container-id>
```

Restart a container:
```bash
docker restart <container-id>
```

Remove a container:
```bash
docker rm <container-id>
```

Open a shell inside a running container:
```bash
docker exec -it <container-id> bash
```

View container logs:
```bash
docker logs <container-id>
```

Give a name to container:
```bash
docker run --name "my-container" nginx
```

<br>

# ⚠️  Common Problems

### Assuming Containers Keep Data Forever

By default, container data is temporary.

Use **Volumes** for persistent storage.

<br>

### Confusing Stopped Containers with Removed Containers

A stopped container still exists.

A removed container no longer exists.

<br>

### Editing Files Inside a Container

Changes made inside a container disappear when the container is removed unless the data is stored in a volume.

<br>

### Running Too Many Containers from the Same Port

Only one container can bind to a specific host port at a time.

<br>

# 💡 Keep in Mind

- A container is a **running instance** of an image.
- Containers are lightweight and isolated.
- Multiple containers can be created from one image.
- Containers share the host OS kernel.
- Containers have a writable layer.
- Removing a container usually removes its writable data.
- Use Volumes to preserve important data.
- Stopping a container is **not** the same as removing it.
