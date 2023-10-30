parent: [[+ rust]]

```rust
fn main() {
    let xs = [0, 100]; // initialise array of length 100 with all 0s
    let ys = [1, 2, 3]; // initialise array with specific elements

    let slice_xs = &[..];
    let slice_xs_to_end = &[50..];
    let slice_xs_from_start = &[..50];
    let slice_xs_start_end = &[25..75];
}
```

- a slice is a reference to an array - it is defined using `&`
