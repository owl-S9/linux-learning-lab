# Docker - Troubleshooting

This file contains real problems I encountered while using Docker and the solutions that worked for me.

The goal is not to document every Docker error, but to build a personal knowledge base of practical issues, debugging steps, and lessons learned.

Every entry in this file is based on real experience.

<br>

## Issue #1

```bash
docker run hello-world

docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```

I assumed it might be a stopped service in systemctl, but Docker wasn't listed there at all.

That's when it hit me — I never actually installed Docker itself. I had only installed the docker-cli package, which is just the command-line client, not the actual Docker daemon.

```bash
sudo apt remove docker-cli
sudo apt install docker.io
```

<br>

## Issue #2

I got a permission error because I installed Docker as root.

Adding my user to the docker group resolved it.

```bash
sudo usermod -aG docker $USER
sudo reboot
```

<br>

## Issue #3

```bash
$ docker command 
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

$ systemctl status docker
Active: failed
(code=exited, status=1/FAILURE)

$ sudo systemctl start docker
Job for docker.service failed because the control process exited with error code.

$ sudo journalctl -u docker.service -e
docker.service: Start request repeated too quickly.
docker.service: Failed with result 'start-limit-hit' # it says i just tried few times, it's enough, i will not try to run it anymore 
Failed to start docker.service - Docker Application Container Engine.
# ...
# going upper
# ...
chmod /var/lib/docker: read-only file system # i find it ???
```

after some time i find something else:
```bash
zsh: locking failed for /home/kali/.zsh_history: read-only file system: reading anyway
```

and now i was sure the problem is more bigger, and its ont just on docker.

something happend to my disk.

```bash
mount | grep "ro,"
/dev/mmcblk0p2 on / type ext4 (ro,relatime) # not ok?

df -h
/dev/mmcblk0p2   59G   16G   40G  29% / # ok

sudo dmesg | grep -i "error\|fail\|read-only"
# no output # maybe ok
```

yes, my disk has been set to read-only mode. :P 

why? i don't know ... still no idea

it just got fixed by: 
```bash
sudo mount -o remount,rw /
```

maybe i should move it to another note that is about linux system, maybe later.

