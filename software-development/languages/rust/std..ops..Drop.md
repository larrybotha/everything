parent: [[+ rust]]

A trait that describes how to free values from memory that are no longer required

e.g. when a value goes out of scope

- generally not required to be implemented, unless the type manages some other resource, e.g.
	- file descriptors
	- sockets
	- memory
- mutually exclusive to [[std..marker..Copy|Copy]] - a type may implement only one or the other trait
## Links and resources

https://doc.rust-lang.org/nightly/std/ops/trait.Drop.html