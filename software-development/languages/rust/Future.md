parent: [[+ rust]]

- a value that may not have finished computing yet
- awaited on using `Future::await`, similar to promises in JavaScript
- futures are polled in an attempt to resolve the future into a final value - the poll method is generally not used directly, but is used internally by the future
- `Future` is a trait that can be implemented on a struct - it is not a struct itself

## links and resources

- https://doc.rust-lang.org/beta/std/future/trait.Future.html