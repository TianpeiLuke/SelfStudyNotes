---
tags:
  - code
  - code_snippet
  - linux
  - docker
keywords: 
topics: 
language: bash
date of note: 2024-04-01
---

## Code Snippet Summary

>[!important]
>The main tasks in this code snippet
>- **Remove** *dangling and unused* docker images in local machine. 
>- Redundant means that there is no reference to given images in container
>- **Remove** all *stopped* containers.  

## Code

- For _unused_ images, use the following command for removing **dangling** _and_ **ununsed** images.

```bash
docker image prune -a
```

- `docker image prune`: Remove all dangling images. If `-a` is specified, also remove all images not referenced by any container.  [reference](https://docs.docker.com/reference/cli/docker/image/prune/)

>[!warning]
>'_unused_' means "images not referenced by any container": be careful before using `-a`.


- To remove all _unused_ images not just dangling ones... which can be a bit too much.

```bash
docker system prune --all
```

- Old answer
```bash
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```

- The `dangling=true` filter finds unused images


- Similarly, to remove all **stopped** containers, we use command

```bash
docker container prune
```

- `docker container prune`: [reference](https://docs.docker.com/reference/cli/docker/container/prune/)
	- `--filter`: The filtering flag (`--filter`) format is of "key=value". If there is more than one filter, then pass multiple flags.
		- until (`<timestamp>`) - only remove containers created before given timestamp
		- label (`label=<key>`, `label=<key>=<value>`, `label!=<key>`, or `label!=<key>=<value>`) - only remove containers with (or without, in case `label!=...` is used) the specified labels.

>[!info]
>A **Docker container** is a running **Docker Image**.
>
>**Docker image** includes programs, dependencies, and environments.



-----------
##  Recommended Notes

- [**`docker system prune`**](https://docs.docker.com/engine/reference/commandline/system_prune/) will delete all dangling data (containers, networks, and images). You can remove all unused volumes with the `--volumes` option and remove all unused images (not just dangling) with the `-a` option.
- [docker base command](https://docs.docker.com/engine/reference/commandline/docker/).


- [[Docker Container]]
- [[Docker Container Images]]
- You also have:
	- [`docker container prune`](https://docs.docker.com/engine/reference/commandline/container_prune/)
	- [`docker image prune`](https://docs.docker.com/engine/reference/commandline/image_prune/)
	- [`docker network prune`](https://docs.docker.com/engine/reference/commandline/network_prune/)
	- [`docker volume prune`](https://docs.docker.com/engine/reference/commandline/volume_prune/)
- Stack overflow: [How to remove old and unused Docker images](https://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images)