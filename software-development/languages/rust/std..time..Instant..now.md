Parent: [[+ rust]]

```rust
use std::time::Instant;

fn do_the_loop(num: &u32) {
    let mut x = 0;

    for _ in 0..*num {
        x += 1;
    }
}

fn main() {
    let timer = Instant::now();

    {
        do_the_loop(&10_000_000);
    }

    let elapsed = timer.elapsed();

    println!("Elapsed: {:.2?}", elapsed);
}
```

- similar to `datetime.now` in Python and `Date.now` in Javascript

## links and resources

- https://doc.rust-lang.org/std/time/struct.Instant.html
