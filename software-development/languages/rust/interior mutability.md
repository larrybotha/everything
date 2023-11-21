parent: [[+ rust]]

- a mechanism for working around Rust's mutability rules by allowing for
  mutation of values that have multiple references
- Interior mutability is great for writing safe applications. Not so much safe libraries - source: https://rust-unofficial.github.io/too-many-lists/fourth-iteration.html#iter
## related

- [[std..sync..Mutex]]
- [[std..rc..RefCell]]