Parent: [[+ git]]

```shell
# get the evolution of changes for a range of lines in a file
$ git log -L 5,10:file.txt

# get the evolution of changes for a function in a file
$ git log -L :func_name:file.txt

# get logs where files contained 'foo'
# Useful for grepping for values that were once, but are no longer in the
# codebase
$ git log -S foo -p
```
