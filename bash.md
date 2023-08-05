
# General

If you have a large amount of files to delete, use xargs:
```
find . -name <pattern of files to delete> | xargs rm -v
```

# Disk space

Use du (disk usage, with -h flag for human readable format) to show the remaining space in a directors

```
du -h
```
