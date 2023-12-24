Parent: [[+ rust]]

```rust
use std::fs::File;
use std::io::prelude::*;

fn main() -> std::io::Result<()> {
    let data = b"some bytes";

    let mut current_pos = 0;
    // File implements std::io::Write
    let mut buffer = File::create("destination.txt")?;

    while current_pos < data.len() {
        // File;:write writes bytes from a slice
        let bytes_written = buffer.write(&data[current_pos..])?;

        // set the next position of the data to write
        current_pos += bytes_written;
    }

    Ok(())
}
```

- a trait that generalises over things that one can write to
- implementers of this trait are sometimes referred to as _writers_. Writers
    have two required methods:
    * `write` - writes data into the object. `write` returns how many bytes were
        written, which is useful as writing from a byte-string requires a loop,
        and for each loop we'd need to know where to begin the next write from
        that byte-string
    * `flush` - ensures that all buffered data has been written to its
        destination
- one can write to strings, [[std..io..stdout]], strings, files, streams,
    vectors of byte-strings, etc.
    * i.e. a function or trait can accept something that implements `Write`, and
        that thing can be passed in, and written to
    * writing to the object that has implemented `Write` can be done with the
        `writeln!` macro, which accepts the object as the first parameter

## links and resources

- https://doc.rust-lang.org/std/io/trait.Write.html
