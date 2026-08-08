# Docker Commands

## Image

```bash
docker build -t <image> .
docker images
docker image ls
docker image inspect <image>
docker image rm <image>
docker pull <image>
docker push <image>
docker tag <image> <new-tag>
docker history <image>
```

<br>

## Container

```bash
docker run <image>
docker run -d <image>
docker run --name <name> <image>
docker run -it <image> bash
docker run -p 8080:80 <image>
docker run -v volume:/path <image>

docker ps
docker ps -a

docker start <container>
docker stop <container>
docker restart <container>
docker pause <container>
docker unpause <container>

docker rm <container>
docker rm -f <container>

docker exec -it <container> bash
docker logs <container>
docker logs -f <container>

docker inspect <container>

docker stats
docker top <container>

docker rename <old> <new>

docker cp file.txt container:/tmp
docker cp container:/tmp/file.txt .
```

<br>

## Volumes

```bash
docker volume create <volume>

docker volume ls

docker volume inspect <volume>

docker volume rm <volume>

docker volume prune
```

<br>

## Networks

```bash
docker network ls

docker network create <network>

docker network inspect <network>

docker network connect <network> <container>

docker network disconnect <network> <container>

docker network rm <network>
```

<br>

## Docker Compose

```bash
docker compose up

docker compose up -d

docker compose down

docker compose build

docker compose ps

docker compose logs

docker compose restart

docker compose stop

docker compose start

docker compose exec app bash
```

<br>

## Registry

```bash
docker login

docker logout

docker search nginx

docker pull nginx

docker push username/image

docker tag image username/image:latest
```

<br>

## System

```bash
docker version

docker info

docker system df

docker system prune

docker system prune -a

docker system events
```

<br>

## Cleanup

```bash
docker container prune

docker image prune

docker image prune -a

docker volume prune

docker network prune

docker system prune

docker system prune -a
```

<br>

## Useful

```bash
docker inspect <object>

docker stats

docker events

docker diff <container>

docker history <image>

docker save -o image.tar <image>

docker load -i image.tar

docker export <container> > container.tar

docker import container.tar
```
