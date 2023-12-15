Parent: [[+ rust]]

```rust
fn main() {
    let mut assignable_path = std::path::PathBuf::new();

    assignable_path.push("foo");
    assignable_path.push("bar");
    assignable_path.push("baz");

    assert_eq!(
        assignable_path.display().to_string(),
        "foo/bar/baz".to_string()
    );
}
```

- an owned mutable path - `PathBuf` is to `Path` as `String` is to `str`
- allows for working with system paths in a cross-platform manner
- all methods on `Path` slices are available on `PathBuf`
- `PathBuf::push` is similar to `Path::join`

## related

- [[std..path..Path]]

## links and resources

- https://doc.rust-lang.org/std/path/struct.PathBuf.html
