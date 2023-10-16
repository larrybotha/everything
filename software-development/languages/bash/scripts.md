parent: [[+ bash]]

- the shebang is formally known as an _interpretive directive
	- when the file is executed guys the bash command, it is treated as a comment:

	```
	$ bash myscript
	```
	- when the file is executed as an application, the OS uses it to determine the interpreter

	```
	$ ./myscript
	```
- don't append `.sh` to bash scripts - it's misleading, and the extension is unnecessary
- `bin` is the folder name commonly used to house commands and executable binaries
	- it's common to use `$HOME/.config/bin` for personal scripts or commands

## Links and resources

https://mywiki.wooledge.org/BashGuide/CommandsAndArguments#Scripts