parent: [[+ bash]]

- parameters are expanded by prefixing them with a `$`
- always double-quote parameter expansions
- parameter expansions are also known as substitutions
## variables

Variables are parameters that are denoted by a name

```shell
# no spaces
$ foo="bar"

# the following is a command that is
# passed an equal sign and text
$ foo = "bar"

# parameter expansion tells bash that
# we want to access the contents of
# a variable
$ echo "$foo"

# always quote variable expression
$ file="my file.png"
$ rm $file 
rm: my: No such file or directory
rm: file.png: No such file or directory

# the above fails because it expands
# s.t. rm receives 2 arguments:
# $ rm my file.png
```

## special parameters

Parameters that *aren't* variables are called *special parameters*

```shell 
# 0, 1, 2, #, *, ?, !, $, _ are
# all special parameters
# we use parameter expansion to
# access their contents 
$ echo "$0" # name or path of script
$ echo "$?" # last command's exit code
$ echo "$1" # first positional param 
$ echo "$*" # all positional params, expands to string 
$ echo "$@" # all positional params, expands to list
$ echo "$#" # expands to number of positional arguments
$ echo "$$" # expands to PIS of current shell 
```

## expansions 

- `${parameter:-word}`
	- **use default value**
	- if `parameter` is unset or null, use `word`, then perform substitution 
- `${parameter:=word}`
	- **assign default value**
	- if `parameter` is unset or null, assign it to `word`, then perform substitution
- `${parameter:+word}`
	- **use alternate value**
	- if `parameter` is unset or null, do not substitute, otherwise substitute `word`
- `${parameter:offset:length}`
	- **get substring or subset of array**
	- `offset` may be negative. Parens required 
- `${#parameter}`
	- **get length of string or array**
- `${parameter#pattern}`
	- **match `pattern` from the beginning of the string, deleting the shortest match**
	- when operating on arrays, operates on each item
- `${parameter##pattern}`
	- **match `pattern` from the beginning of the string, deleting the longest match**
	- greedy equivalent of single `#`
	- e.g. is analogous to `basename`:
		```shell
		x="foo/bar/baz.png"
		echo "${x##*/}" # => bax.png
		```
- `${parameter%pattern}`
	- **match `pattern` from the end of the string, deleting the shortest match**
	- e.g. is analogous to `dirname`:
		```shell
		x="foo/bar/baz.png"
		echo "${x%/*}" # => foo/bar
		```
- `${parameter%%pattern}`
	- **match `pattern` from the end of the string, deleting the longest match**
	- greedy equivalent of single `%`
- `${parameter/pat/string}`
	- **substitute the first instance of `pat` for `string`**
	- works similarly to Vim's [[substitute - vim]]
- `${parameter//pat/string}`
	- **substitute all instance of `pat` for `string`**
	- works similarly to Vim's [[substitute - vim]] with the global flag 
- `${parameter/#pat/string}`
	- **substitute the first instance of `pat` for `string` from the beginning of the string**
	- can be used to add a suffix:
		```shell
		x="bar.png"
		echo "${x/#/foo/}" # => foo/bar.png
```
- `${parameter/%pat/string}`
	- **substitute the first instance of `pat` for `string` from the beginning of the string**
	- can be used to add a suffix:
		```shell
		x="bar.png"
		echo "${x/%/.bak}" # => bar.png.bak
```
## Links and resources

- https://mywiki.wooledge.org/BashGuide/Parameters
- https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Shell-Parameter-Expansion