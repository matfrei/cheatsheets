# Useful commands in docker

## Building and deployoing containers

### Build a docker container
```
docker build -f /path/to/Dockerfile -t repo.url.com:1234/username/reponame/containername:tag  --build-arg CACHEBUST=$(date +%s) ./.
```

### Login to a container registry

Ideally you should use a token created speficially for that use. Export your token as an environment variable:

```
export CR_PAT=YOUR_TOKEN
```

Then, log in to the registry using

```
echo $CR_PAT | docker login repo.url.com:1234 -u username --password-stdin
```

### Push a built container to a registry
```
docker push repo.url.com:1234/username/reponame/containername:tag
```

## Using containers

### Start a container with GPU support

```
docker run --gpus all -it -d -p 8080:8080 minedojo/minedojo:latest tail -f /dev/null
```

### Stop a container

```
docker stop <running_container_id>
```

### See which images are currently pulled
```
docker images
```

### See which containers are currently running

```
docker ps
```

### Interact with a running docker container

```
docker exec -it <running_container_id> /bin/bash
```
**Hint:** When working with container ids, there is no need to copy the full id, only enough to make the id unique among the containers on the system

For instance, if I have two containers on my system with ids ``9446123a7c1a0575e689623222b9df70d509715218e443c38fbc4e03029336d5``and ``13fce77a7c84450a679caaaa6df030711010b3490dd5c86c627d08dc008d2b47``, I can get a shell on the latter container simply by executing:

``
docker exec -it 1 /bin/bash
``

since only one of the available containers has an id that starts with ``1``.

### Instantiate a container from a docker image and get an immediate shell in the container 

```
docker run -t -i --rm --entrypoint bash repo.url.com:1234/username/reponame/containername:tag
```

## Transferring files to and from containers

```
docker cp /path/to/localfile <running_container_id>:/path/in/container/
```

## Clearing all containers from a machine when things have gone bad and a fresh start is needed

(or you have filled the harddisk with lots of docker images and disk space is urgently needed)

```
docker system prune --all
```

## Reconstruct a dockerfile from the container 

```
sudo docker history --no-trunc repo.url.com:1234/username/reponame/containername  | tac | tr -s ' ' | cut -d " " -f 5- | sed 's,^/bin/sh -c #(nop) ,,g' | sed 's,^/bin/sh -c,RUN,g' | sed 's, && ,\n  & ,g' | sed 's,\s*[0-9]*[\.]*[0-9]*\s*[kMG]*B\s*$,,g' | head -n -1 >> backup_docckerfile.txt
```

## Bash-script to be used as a post-commit-hook

```
#!/bin/bash
set -ex
BASE_DIR="$(git rev-parse --show-toplevel)"
REPO="$(git config --get remote.origin.url | sed 's/.*://;s/.git$//')"
REGISTRY="repo.url.com:1234"
docker build -f "${BASE_DIR}"/path/to/Dockerfile -t "${REGISTRY}"/"${REPO}":latest "${BASE_DIR}"/.
docker push "${REGISTRY}"/"${REPO}":latest
```
