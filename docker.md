# Useful commands in docker

## Building containers

```
sudo docker build -f /path/to/Dockerfile -t repo.url.com:4567/username/reponame/containername:tag  --build-arg CACHEBUST=$(date +%s) ./.
```

## Using containers

### Start a container with GPU support

```
docker run --gpus all -it -d -p 8080:8080 minedojo/minedojo:latest tail -f /dev/null
```

### See which containers are currently running

```
docker ps
```

### Interact with a running docker container

```
docker exec -it <running_container_id> /bin/bash
```

### Instantiate a container from a docker image and get an immediate shell in the container 

```
docker run -t -i --rm --entrypoint bash repo.url.com:4567/username/reponame/containername:tag
```

## Transferring files to and from containers

```
sudo docker cp /path/to/localfile hungry_ishizaka:/path/in/container/
```

## Reconstruct a dockerfile from the container 

```
sudo docker history --no-trunc repo.url.com:4567/username/reponame/containername  | tac | tr -s ' ' | cut -d " " -f 5- | sed 's,^/bin/sh -c #(nop) ,,g' | sed 's,^/bin/sh -c,RUN,g' | sed 's, && ,\n  & ,g' | sed 's,\s*[0-9]*[\.]*[0-9]*\s*[kMG]*B\s*$,,g' | head -n -1 >> backup_docckerfile.txt
```

## Bash-script to be used as a post-commit-hook

```
#!/bin/bash
set -ex
BASE_DIR="$(git rev-parse --show-toplevel)"
REPO="$(git config --get remote.origin.url | sed 's/.*://;s/.git$//')"
REGISTRY="repo.url.com:4567"
docker build -f "${BASE_DIR}"/gpulab/Dockerfile -t "${REGISTRY}"/"${REPO}":latest "${BASE_DIR}"/.
docker push "${REGISTRY}"/"${REPO}":latest
```
