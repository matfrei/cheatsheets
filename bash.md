If you have a large amount of files to delete, use xargs:
```
find . -name <pattern of files to delete> | xargs rm -v
```
