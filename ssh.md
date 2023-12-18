# SSH


## ssh loopback
```
ssh user@hostname -L <localport>:<dst_hostname>:<remoteport>
```
e.g.
```
ssh user@hostname -L 8888:127.0.0.1:8888
```
## set up an .ssh config
from https://linuxize.com/post/using-the-ssh-config-file/
### make sure .ssh config dir exists
```
mkdir -p ~/.ssh && chmod 700 ~/.ssh
```

### create config file and set permissions correctly
```
touch ~/.ssh/config
chmod 600 ~/.ssh/config
```

### file structure and patterns
```
Host hostname1
    SSH_OPTION value
    SSH_OPTION value

Host hostname2
    SSH_OPTION value

Host *
    SSH_OPTION value
```
