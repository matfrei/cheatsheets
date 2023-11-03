
# General

If you have a large amount of files to delete, use xargs:

```
find . -name <pattern of files to delete> | xargs rm -v
```

# User management

Change password for user

```
sudo passwd <username>
```

Login as user

```
sudo su <username>
```

# Disk space

Use du (disk usage, with -h flag for human readable format) to show the remaining space in a directors

```
du -h
```
# Open ports

Output the ports the machine is listening on

```
sudo lsof -i | grep LISTEN
```

# Package management

## Debian-style systems using apt

## Doing upgrades

Package upgrades

```
apt-get update && apt-get upgrade
```

Distro upgrades

```
sudo do-release-upgrade
```

### Fix broken and held back packages

Broken packages

```
sudo apt install --fix-broken
```

"Package \<xxx\> has been held back"

```
sudo apt install --upgrade <xxx>
```
