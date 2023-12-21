Parent: [[+ rust]]

```rust
use std::io::{BufWriter, Write};

fn slow_writes(&num: u32) {
    for x in 0..num {
        println!("sync printing {x}")
    }
}

fn buffered_writes(&num: u32) {
    let stdout = std::io::stdout();
    let mut handle = BufWriter::new(stdout);

    for x in 0..num {
        writeln!(handle, "buff printing {x}");
    }
}

fn main() {
    let num_writes = 50;

    slow_writes(&num_writes);
    buffered_writes(&num_writes);
}
```

- as with `BufReader`, things that `Write` frequently, such as `println!`, can
    be expensive. By sending values to a `BufWriter`, we can write in large
    infrequent batches
- `BufWriter` is useful for programs that perform small and frequent writes to
    files or sockets

    It provides little to no benefit for large or infrequent writes
- to write data immediately, `BufWriter::flush` can be called
- `BufWriter::flush` must be called before the writer is dropped. If the writer
    isn't flushed dropped, there's a possibility that data will be written to
    the underlying stream

## related

- [[std..io..BufReader]]

## links and resources

- https://doc.rust-lang.org/std/io/struct.BufWriter.html
- https://rust-cli.github.io/book/tutorial/output.html#a-note-on-printing-performance
