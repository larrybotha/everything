parent: [[+ rust]]

- allows for implementing the _interior mutability pattern_ which is a mechanism for working around Rust's mutability rules by allowing for mutation of values that have multiple references

## Relations

- [[std..rc..Rc]] - multiple references are by default immutable - wrapping the contents of `Rc` allows for mutation of these values