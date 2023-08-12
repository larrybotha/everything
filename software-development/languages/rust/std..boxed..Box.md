parent: [[+ rust]]

- a type that represents a pointer to a value allocated on the heap
- has exclusive ownership of the allocation:
	- dropping the box will drop its content
	- the value is mutable, since only 1 reference may exist at a time
- useful when there is no need to have multiple references to the allocation

## Relations

- [[std..rc..Rc]] - has features which contrast with `Box`