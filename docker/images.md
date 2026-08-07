# Docker - Images

> Learn what Docker Images are, how they work, and why they are the foundation of containers.

<br>

# 🧠 Main Idea

A **Docker Image** is a read-only template used to create containers.

It contains everything an application needs to run, including the application code, runtime, libraries, dependencies, and configuration.

One image can be used to create multiple containers.

<br>

# 🤔 Why Do We Need It?

Without images, Docker would have no blueprint for creating containers.

Images provide:

- Portability
- Consistency
- Reproducibility
- Easy sharing
- Fast deployment

An application behaves the same regardless of where the image is executed.

<br>

# 📦 Concept

### What is an Image?

Think of an image as a **blueprint** or **template**.

It is not running.

It only contains the instructions and files required to create a container.

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

### What's Inside an Image?

A Docker image may contain:

- Application source code
- Runtime (Python, Node.js, Java, etc.)
- Libraries
- Dependencies
- Environment variables
- Configuration files
- Default startup command

<br>

### Image Layers

Docker images are built in **layers**.

Each instruction in a Dockerfile usually creates a new layer.

Example:

```text
Ubuntu Base Image
        │
        ▼
Install Python
        │
        ▼
Install Packages
        │
        ▼
Copy Application
        │
        ▼
Final Image
```

Layers are cached and reused whenever possible, making image builds faster and more efficient.

<br>

### Image Lifecycle

```text
Dockerfile
      │
      ▼
Build Image
      │
      ▼
Docker Image
      │
      ▼
Push / Pull
      │
      ▼
Run Container
```

<br>

### Image Tags

Tags identify different versions of an image.

Example:

```text
python:3.12
python:3.11
nginx:latest
ubuntu:24.04
```

Without a tag, Docker automatically uses latest version.

<br>

### Where Images Are Stored

Images are stored:

- Locally on your machine
- In a Docker Registry (such as Docker Hub)

When Docker cannot find an image locally, it attempts to download it from a registry.

<br>

# 🔍 Examples

Download an image:
```bash
docker pull nginx
```

List local images:
```bash
docker images
```

Inspect an image:
```bash
docker image inspect nginx
```

Remove an image:
```bash
docker rmi nginx
```

Build an image from a Dockerfile:
```bash
docker build -t myapp .
```

<br>

# ⚠️  Common Problems

### Confusing Images with Containers

An image is a template.

A container is a running instance of that template.

<br>

### Using the Wrong Tag

Different tags may contain different software versions.

Always verify the tag before using an image.

<br>

### Assuming Images Change Automatically

Images are immutable.

If the application changes, a new image must be built.

<br>

### Deleting an Image Used by Containers

Docker prevents removing an image while containers still depend on it.

Remove the containers first or use the force option if appropriate.

<br>

# 💡 Keep in Mind

- Images are **read-only**.
- Containers are created from images.
- One image can create many containers.
- Images are built from Dockerfiles.
- Images consist of multiple layers.
- Layers improve build speed through caching.
- Images can be stored locally or in registries.
- Tags identify image versions.
- Images are immutable; modifying an application requires building a new image.
