Parent: [[+ rust]]

- using `Read` can be expensive - `BufReader` performs large infrequent reads on
    the underling `Read`, maintaining an in-memory buffer of results
- use when the following conditions are true:
    * reads are small
    * reads are repeated
    * reads are on the same file or network socket
- not useful when:
    * reading large amounts at once
    * reading only once or a few times
    * reading from a source that is already in memory

## links and resources

- https://doc.rust-lang.org/std/io/struct.BufReader.html