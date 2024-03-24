Parent: [[+ bash]]

(*Unix* is a more accurate parent)


- indicates where a string terminates, e.g.
	- defining strings in C
	- the end of the file for a SQLite database
- represented as `$'\0'`
- command [[bash arguments|arguments]] cannot contain null bytes
- strings processed by the shell will terminate at the first encountered null byte