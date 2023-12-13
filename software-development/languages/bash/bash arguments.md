---
aliases:
  - arguments
---
Parent: + bash

- along with understanding [[word  splitting]], arguments in bash are fundamental to writing bash scripts
- arguments to commands are strings, and strings can contain any characters *except* the [[NUL byte]]
- unlike many programming languages, white space is critical to bash - whether something is a space or tab is significant 
- executing commands happens via the `execve(2)` system call which requires 3 pieces of info:
	- the file to execute, i.e. binary or script
	- array of arguments
	- array of env vars
- bash uses [[word  splitting]] on commands to strip whitespace in preparation for `execve(2)`:
  
```
    rm myfile myotherfile
      ^      ^

    [rm]
    [myfile]
    [myotherfile]
```

- [[IFS]] is used to determine which characters to use as word splitting delimiters 
	- read the associated note on when and when not to modify `IFS` - it's usually best to avoid modifying it
	- to avoid modifying `IFS`:
		- use an array, or
		- set `IFS` on the same line as the command, or
		- use `IFS` in a while-read loop
- use double quotes to prevent [[word  splitting]] and glob expansion
- use single quotes for literal values, e.g.
	```shell
	echo '&' # echo literal ampersand
	```
- double-quoting `$@` or `$array[@]` expands to a list of words
- double-quoting `$*` or `$array[*]` expands to a single word, joined by the first value of `IFS`
	- this is similar to `join` in other languages
## links and resources

- https://mywiki.wooledge.org/Arguments
- https://mywiki.wooledge.org/Quotes