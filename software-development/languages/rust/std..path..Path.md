Parent: [[+ rust]]

```rust
use std::path::Path;

fn main() {
    let path = Path::new("foo/bar");

    assert_eq!(path.parent(), Some(Path::new("foo")));
}
```

- a slice of an OS path
- `Path` is akin to `str`, and is thus _unsized_ - it should always be used
    behind a reference or pointer, such as `Box`
- allows for operating on a path, e.g. splitting it into parts, getting
    basenames, extensions, determining if the path is relative vs absolute,
    getting parents, etc.

## related

- [[std..path..PathBuf]]

## links and resources

- https://doc.rust-lang.org/std/path/struct.Path.html
