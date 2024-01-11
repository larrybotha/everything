Parent: [[+ rust]]

```rust
fn main() -> Result<(), io::Error> {
    let listener = TcpListener::bind("127.0.0.1:0")?;

    for stream in listener.incoming() {
        let stream = stream?;

        // do something with stream
    }

    Ok(())
}
```

- create a TCP listener by binding it to a socket address on the host
  - a socket is a client-server connection between processes on a network
- incoming connections can be handled by:
  - iterating over the `Incoming` iterarator at `TcpListener::incoming`
  - calling `TcpListener::accept`

## links and resources

- https://doc.rust-lang.org/1.74.1/std/net/struct.TcpListener.html
