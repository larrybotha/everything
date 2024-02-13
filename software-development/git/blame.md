Parent: [[+ git]]

```shell
# blame on a range of lines
$ git blame -L 5,10

# blame, but ignore whitespace
$ git blame -w

# blame:
#		- first C: and detect lines moved or copied in the same commit
#		- second C: or the commit that created the file
#		- third C: or any commit at all
# This is arguably a more meaningful way to use blame, even though it takes
# longer to execute
git blame -C -C -C
```
