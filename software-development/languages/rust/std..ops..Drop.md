parent: [[+ rust]]

A trait that describes how to free values from memory that are no longer required

e.g. when a value goes out of scope

- generally not required to be implemented, unless the type manages some other resource, e.g.
	- file descriptors
	- sockets
	- memory
- working with smart pointers, such as [[std..boxed..Box]] and [[std..rc..Rc]], should make one aware that there may be implications regarding `Drop`
	- if a smart pointer owns its value, such as with [[std..boxed..Box]], it will automatically drop its value when it is dropped - beware of double free errors (see https://rust-unofficial.github.io/too-many-lists/fifth-layout.html#layout)
	- if a smart pointer holds a reference to another value, and we don't ensure that *that* value is dropped before our smart pointer, we may end up with dangling pointers (see https://rust-unofficial.github.io/too-many-lists/first-drop.html)
- mutually exclusive to [[std..marker..Copy|Copy]] - a type may implement only one or the other trait
## Links and resources

https://doc.rust-lang.org/nightly/std/ops/trait.Drop.html