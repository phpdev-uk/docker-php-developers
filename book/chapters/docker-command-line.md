# Docker on the Command Line

Before working with more advanced tools such as Docker Composer, it's important to learn the basics of using Docker on the command line. We've already seen an example of this in the introduction:

```bash
$ docker run hello-world
```

`docker run` will run the named image, downloading it if necessary (if it doesn't already exist or a newer version is available).

A more advanced example can be seen by running the Debian image:

```bash
$ docker run debian
```

Containers only run as long as their main process. You can see this by running `docker ps`, which shows all running containers:

```bash
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

However, containers are not removed once they have stopped. The `docker ps` command with `--all` (or `-a`) will show all containers, regardless of status:

```bash
$ docker ps --all
CONTAINER ID   IMAGE                 COMMAND                  CREATED              STATUS                          PORTS     NAMES
29be573bfc95   debian                "bash"                   16 seconds ago       Exited (0) 15 seconds ago                 sleepy_chatelet
```

You can remove a stopped container with `docker rm` followed by either the container ID or the randomly generated container name:

```bash
$ docker rm 29be573bfc95
29be573bfc95

$ docker rm sleepy_chatelet
sleepy_chatelet
```

To see only containers which have stopped, use the `--filter` (or `-f`) option:

```bash
$ docker ps --all --filter status=exited
```

`docker ps` also has a `--quiet` (or `-q`) option which only lists the container IDs. You can combine this with `docker rm` to remove **all** stopped containers:

```bash
$ docker rm $(docker ps --all --quiet --filter status=exited)
```

You may want to create an alias or shell script for the above command, e.g. as `docker-rm-all`.

Docker can also remove containers as soon as they stop with the `--rm` option:

```bash
$ docker run --rm debian
```

## Docker cleanup

An example script that will stop all running containers, remove all stopped containers, and prune any unused volumes (prompting to make sure this is what you want):

```bash
#!/bin/bash

docker stop $(docker ps -aq)
docker rm -v $(docker ps -aq -f status=exited)
docker volume prune
```

This will effectively reset all your Docker environments, so run this script with caution. It will not delete any images on disk, so you will not need to download them again.


