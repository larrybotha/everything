Parent: [[+ rust]]

```rust
// https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=51a4d26130bb436ef40d1ad45d477ee8
use std::io::{BufWriter, Error, Write};
use std::time::Instant;

fn slow_writes(num: &u32) {
    for x in 0..(*num) {
        println!("sync printing {x}")
    }
}

fn buffered_writes(num: &u32) -> Result<(), Error> {
    let stdout = std::io::stdout();
    let mut handle = BufWriter::new(stdout);

    for x in 0..(*num) {
        writeln!(handle, "buff printing {x}")?;
    }

    handle.flush()?;

    Ok(())
}

fn main() -> Result<(), Error> {
    let num_writes = 50;
    let timer = Instant::now();

    slow_writes(&num_writes);

    let duration_slow_writes = timer.elapsed();

    println!("slow_writes duration: {:?}\n", duration_slow_writes);

    let timer = Instant::now();

    buffered_writes(&num_writes)?;

    let duration_buffered_writes = timer.elapsed();

    println!("buffered_writes duration: {:?}\n", duration_buffered_writes);

    println!(
        "buffered writes took {:?} the time of slow writes took",
        duration_buffered_writes.as_secs_f64() / duration_slow_writes.as_secs_f64()
    );

    Ok(())
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
