---
title: "Docker"
weight: 3
---

### Images

Docker images of the siridb-server are available on [GitHub](https://github.com/SiriDB/siridb-server/pkgs/container/siridb-server).

**Supported tags**:

`ghcr.io/siridb/siridb-server:VERSION` _(Minimal SiriDB image based on Alpine Linux.)_

`ghcr.io/siridb/siridb-server:latest` _(Latest SiriDB build from the `master` branch using a minimal Alpine Linux base image)_

### Getting started

The basic steps required to run the SiriDB server in Docker are explained below.

#### Pulling

To get started, run the following command in your terminal:

```bash
$ docker pull ghcr.io/siridb/siridb-server:latest
```

> **Note**: Depending on how you've installed docker on your system, you might see a permission denied error after running the above command. If you're on Linux, you may need to prefix your docker commands with `sudo`. Alternatively you can create a Docker group to get rid of this issue.

The pull command fetches the latest siridb-server image from the GitHub Container Registry and saves it in your system.

#### Running

Great! Let's now run a Docker container based on this image. To do that you are going to use the `docker run` command.

```bash
$ docker run --name siridb -d -p 9000:9000 -v ~/siridb-data:/var/lib/siridb ghcr.io/siridb/siridb-server
```

You’ll notice a few flags being used. Here’s some more info on them:

- `-d` - Run the container in detached mode (in the background).
- `-p 9000:9000` - Map port 9000 of the host to port 9000 (SiriDB port for client socket connections) in the container.
- `-v ~/siridb-data:/var/lib/siridb` - Mount a volume for SiriDB data. (For data persistence)
- `ghcr.io/siridb/siridb-server` - The image to use.

To verify that the container is running, you can use the `docker ps` command.

```bash
$ docker ps
```

This command shows you all containers that are currently running and should display a similar output as this:

```bash
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS         PORTS                                                                     NAMES
a57597077abb   ghcr.io/siridb/siridb-server   "/usr/local/bin/siri…"   4 seconds ago   Up 3 seconds   8080/tcp, 9010/tcp, 9080/tcp, 0.0.0.0:9000->9000/tcp, :::9000->9000/tcp   siridb
```

#### Stopping

To stop the active SiriDB container, run the `docker stop` command.

```bash
$ docker stop siridb
```
