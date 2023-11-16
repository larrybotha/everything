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

  e.g

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

## links and resources

- https://mywiki.wooledge.org/IFS