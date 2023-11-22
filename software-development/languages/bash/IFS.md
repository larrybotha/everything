---
aliases:
  - input field separator
---

Parent: [[+ bash]]

- a string of characters which are treated as delimiters when splitting a line of input
- the default value for `IFS` is _space_, _tab_, _newline_, which it defaults to if it is unset, too 

  i.e.
```shell
IFS=$' \t\n'
```
- setting `IFS` to an empty string results in no word splitting

  e.g.

```shell
$ IFS= read -r a b c <<< 'the plain gold ring'
$ echo "=$a="
=the plain gold ring=

# c acts like Python and JavaScript's rest variable
$ IFS=$' \t\n' read -r a b c <<< 'the plain gold ring'
$ echo "=$c="
=gold ring=

$ IFS=: read -r a b c <<< '1:2:::3::4'
$ echo "=$a= =$b= =$c="
=1= =2= =::3::4=
```
- used in:
	- the `read` command when splitting input into multiple variables
	- trimming whitespace of values in the `read` command
	- [[word  splitting]] on unquoted expansions
	- when performing `$*` or `${array [*]}` expansion
- `IFS` is *only* used in word splitting of **data**, *not* lines of script. Lines of script are always split by whitespace

  e.g.

```shell
IFS=:
# execute a line of script
rm file1 file2:file3

# expands to
# [rm]
# [file1]
# [file2:file3]

files='file1 file2:file3'
rm $files

# expands first to
# [rm]
# ["$files"]
# 
# then IFS is applied to the data,
# resulting in
# [rm]
# [file1 file2]
# [file3]
```

## links and resources

- https://mywiki.wooledge.org/IFS
- https://mywiki.wooledge.org/Arguments