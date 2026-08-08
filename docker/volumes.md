# Docker - Volumes

> Docker Volumes provide persistent storage for containers.

<br>

# 🧠 Main Idea

A **Docker Volume** is a persistent storage mechanism managed by Docker.

Unlike a container's writable layer, a volume exists independently of the container, allowing data to remain even after the container is stopped or removed.

<br>

# 🤔 Why Do We Need It?

Containers are designed to be temporary.

If important data is stored only inside a container, removing that container usually removes the data as well.

Volumes solve this problem by storing data outside the container.

They provide:

- Persistent storage
- Data sharing between containers
- Better performance
- Easier backups and migration

<br>

# 📦 Concept

### What is a Volume?

A volume is a special directory managed by Docker.

It is mounted into a container, allowing applications to read and write data while keeping that data independent of the container itself.

```text
Container
     │
     │ Read / Write
     ▼
Docker Volume
```

If the container is removed, the volume still exists.

<br>

### Why Not Store Data Inside Containers?

Container storage is temporary.

When the container is deleted, its writable layer is usually deleted as well.

Using a volume separates application data from the container lifecycle.

<br>

### Volume Lifecycle

```text
Create Volume
      │
      ▼
Attach to Container
      │
      ▼
Application Reads/Writes Data
      │
      ▼
Remove Container
      │
      ▼
Volume Still Exists
```

<br>

## Types Of Voluems

<br>

### Named Volumes

A named volume has a user-defined name.

Example:

```bash
docker volume create my-data
```

Use it with a container:

```bash
docker run -v my-data:/app/data nginx
# -v host:container
```

Docker manages the storage location automatically.

<br>

### Anonymous Volumes

Docker can create volumes automatically without assigning a name.

These volumes are harder to manage because Docker generates random names.

Named volumes are generally preferred.

<br>

### Host Volumes (Bind Mounts)

A bind mount maps a specific directory or file from the host machine directly into a container.

<br>

## Bind Mount vs Volume

### Volume

- Managed by Docker
- Stored in Docker's data directory
- Best for persistent application data

<br>

### Bind Mount

- Uses an existing directory on the host
- Files are directly accessible from the host
- Commonly used during development

Example:

```bash
docker run -v $(pwd):/app nginx
```

<br>

## List and Inspect Volumes

List volumes:
```bash
docker volume ls
```

Inspect a volume:
```bash
docker volume inspect my-data
```

Remove a volume:
```bash
docker volume rm my-data
```

<br>

# 🔍 Examples

Create a volume:

```bash
docker volume create postgres-data
```

Run PostgreSQL using the volume:

```bash
docker run -d \
-v postgres-data:/var/lib/postgresql/data \
postgres
```

List volumes:

```bash
docker volume ls
```

Inspect a volume:

```bash
docker volume inspect postgres-data
```

Remove a volume:

```bash
docker volume rm postgres-data
```

Remove unused volumes:

```bash
docker volume prune
```

<br>

# ⚠️  Common Problems

### Assuming Container Storage Is Permanent

Container storage disappears when the container is removed.

Use volumes for important data.

<br>

### Removing a Volume Accidentally

Deleting a volume permanently deletes its data.

Always verify before running:

```bash
docker volume rm
```

or

```bash
docker volume prune
```

<br>

### Confusing Volumes with Bind Mounts

Volumes are managed by Docker.

Bind mounts use directories from the host machine.

They serve different purposes.

<br>

### Forgetting to Mount the Volume

Creating a volume alone is not enough.

The container must mount it to use it.

<br>

# 💡 Keep in Mind

- Volumes provide persistent storage.
- Volumes exist independently of containers.
- Removing a container does not remove its volumes.
- Docker manages the storage location of volumes.
- Named volumes are easier to manage than anonymous volumes.
- Bind mounts and volumes are different concepts.
- Volumes are the recommended choice for databases and application data.
- `docker volume ls` lists all volumes.
- `docker volume prune` removes all unused volumes.
