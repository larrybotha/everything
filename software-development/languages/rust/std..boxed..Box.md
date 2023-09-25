parent: [[+ rust]]

- a type that represents a pointer to a value allocated on the heap
- has exclusive ownership of the allocation:
	- dropping the box will drop its content
	- the value is mutable, since only 1 reference may exist at a time
- useful when there is no need to have multiple references to the allocation
- automatically drops its contents when it goes out of scope
	- thus does not implement [[std..marker..Copy|Copy]] - i.e. it has [[move semantics]]

## Relations

- [[std..rc..Rc]] - has features which contrast with `Box`

## Links and resources

- https://doc.rust-lang.org/nightly/std/boxed/index.html