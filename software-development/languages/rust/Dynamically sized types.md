Parent: [[+ rust]]

- also known as *DST*s
- types where the size is not known at compile time
	- most types have a fixed size, and are known at compile time. See [[Sized]]
- [[slice]]s and [[trait objects]] are two common DSTs
- pointer types, i.e. references, raw pointers, and smart pointers, that point to DSTs occupy twice the memory that pointers to sized types
	- pointers to slices store the number of elements in the slice
	- pointers to trait objects store a reference to a vtable
- denoted by the `?Sized` trait bound in generic functions
- `Self: ?Sized` is the default in trait definitions
- structs may contain a DST as the last field, which makes the struct a DST itself

## links and resources

- https://doc.rust-lang.org/reference/dynamically-sized-types.html