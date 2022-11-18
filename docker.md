# Useful commands in docker


### see which containers are currently running

```
docker ps
```

## Reconstruct a dockerfile from the container 
```
sudo docker history --no-trunc repo.url.com:4567/matfrei/reponame/containername  | tac | tr -s ' ' | cut -d " " -f 5- | sed 's,^/bin/sh -c #(nop) ,,g' | sed 's,^/bin/sh -c,RUN,g' | sed 's, && ,\n  & ,g' | sed 's,\s*[0-9]*[\.]*[0-9]*\s*[kMG]*B\s*$,,g' | head -n -1 >> backup_docckerfile.txt
```
