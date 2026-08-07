# Docker - Dockerfile

> Learn how to build custom Docker Images using a Dockerfile.

<br>

# 🧠 Main Idea

A **Dockerfile** is a text file that contains a series of instructions for building a Docker Image.

Instead of creating images manually, you describe how the image should be built, and Docker follows those instructions step by step.

It's acctually a blueprint.

<br>

# 🤔 Why Do We Need It?

Without a Dockerfile, building images would be manual, slow, and difficult to reproduce.

A Dockerfile allows you to:

- Automate image creation.
- Create reproducible environments.
- Version-control your image configuration.
- Share application environments easily.
- Build images consistently on any machine.

<br>

# 📦 Concept

### What is a Dockerfile?

A Dockerfile is simply a text file named:

```text
Dockerfile
```

It contains instructions that Docker executes from top to bottom to build an image.

Example:

```text
Dockerfile
      │
      ▼
docker build
      │
      ▼
Docker Image
      │
      ▼
Container
```

<br>

### Build Process

When Docker builds an image, it executes each instruction one by one.

Most instructions create a new **layer**.

```text
  Dockerfile
      │
      ▼
    FROM
      │
      ▼
     ENV
      │
      ▼
     RUN
      │
      ▼
    COPY
      │
      ▼
     CMD
      │
      ▼
 Docker Image
```

Docker caches layers whenever possible, making future builds much faster.

<br>

### Basic Dockerfile Example

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```

This Dockerfile:

- Starts from a Python image.
- Creates a working directory.
- Copies project files.
- Installs dependencies.
- Runs the application.

<br>

## Common Instructions

### FROM

Specifies the base image.

```dockerfile
FROM ubuntu:24.04
```

Every Dockerfile usually begins with `FROM`.

<br>

### WORKDIR

Sets the working directory.

```dockerfile
WORKDIR /app
```

<br>

### COPY

Copies files from the host into the image.

```dockerfile
COPY . .
```

<br>

### ADD

Similar to `COPY`, but supports URLs and automatic archive extraction.

For most cases, prefer `COPY`.

<br>

### RUN

Executes commands while building the image.

```dockerfile
RUN apt update
```

<br>

### ENV

Defines environment variables.

```dockerfile
ENV APP_ENV=production
```

<br>

### EXPOSE

Documents the port used by the application.

```dockerfile
EXPOSE 8080
```

<br>

### CMD

Specifies the default command when the container starts.

```dockerfile
CMD ["python", "app.py"]
```

Only one `CMD` should exist in a Dockerfile.

Its changeable.

<br>

### ENTRYPOINT

Defines the main executable for the container.

Unlike `CMD`, it is intended to always run.

Example:

```dockerfile
ENTRYPOINT ["python"]
```

It's unchangeable.

<br>

## Build an Image

```bash
docker build -t myapp .
```

Explanation:

- `-t` → Image tag
- `myapp` → Image name
- `.` → Current directory (build context)

<br>

### Build Context

The build context is the directory sent to Docker during the build process.

Everything inside this directory can be accessed by `COPY` and `ADD`.

```text
Project/
│
├── Dockerfile
├── app.py
├── requirements.txt
└── src/
```

Running:

```bash
docker build .
```

sends the entire project directory as the build context.

<br>

# 🔍 Examples

Build an image:
```bash
docker build -t myapp .
```

Build with a specific Dockerfile:
```bash
docker build -f Dockerfile.dev -t myapp .
```

Build without using cache:
```bash
docker build --no-cache -t myapp .
```

Run the image:
```bash
docker run myapp
```

<br>

# ⚠️ Common Problems

### Forgetting the Build Context

The final `.` in:
```bash
docker build -t myapp .
```

is required.

It specifies the build context.

<br>

### Using ADD Instead of COPY

Use `COPY` unless you specifically need features provided by `ADD`.

<br>

### Placing Frequently Changed Files Too Early

Docker rebuilds layers after a changed instruction.

Place files that change often near the end of the Dockerfile to maximize layer caching.

<br>

### Multiple CMD Instructions

Only the last `CMD` instruction is used.

Earlier ones are ignored.

<br>

### Confusing Dockerfile with Docker Compose

Dockerfile builds **one image**.

Docker Compose manages **multiple containers**.

<br>

# 💡 Keep in Mind

- A Dockerfile builds a Docker Image.
- The file name is `Dockerfile`.
- Instructions are executed from top to bottom.
- Most instructions create image layers.
- Docker caches layers to speed up builds.
- Every Dockerfile usually starts with `FROM`.
- `RUN` executes commands during image build.
- `CMD` defines the default startup command.
- `ENTRYPOINT` defines the main executable.
- `COPY` is generally preferred over `ADD`.
- `docker build` creates an image from a Dockerfile.
- The build context determines which files Docker can access.
