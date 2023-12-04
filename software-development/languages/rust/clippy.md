parent: [[+ rust]]

```rust
use std::f32;

#[allow(clippy::approx_constant)]
fn main() {
    let pi = 3.14f32;
}
```

- the `allow` attribute allows denied lints to be ignore
- `allow` is one of 5 _lint levels_ in Rust - see the
  [lint levels](https://doc.rust-lang.org/1.74.0/rustc/lints/levels.html) docs

## links and resources

- [Clippy Lints](https://rust-lang.github.io/rust-clippy/stable/index.html)
- [Lint levels](https://doc.rust-lang.org/1.74.0/rustc/lints/levels.html)
