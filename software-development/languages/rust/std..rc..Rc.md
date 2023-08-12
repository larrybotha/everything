parent: [[+ rust]]

- a pointer type that allows for reference counting of heap-allocated values
	- multiple references to the value may exist at the same time, and thus
	- the value is immutable
 - useful when shared references to values are required
 - if interior mutability is required, needs to be used in conjunction with [[std..rc..RefCell]]

## Relations

- [[std..boxed..Box]] - contrasts with Box
- [[std..rc..RefCell]] - required for mutating the contents of `Rc`
