Parent: [[+ rust]]

```shell
# run a binary from the project root
$ cargo run [binary-name] [...args]

# evaluate what macros expand to
$ cargo rustc --profile=check -- -Zunpretty=expanded
# or, after installing cargo-expand
$ cargo expand
# or, for a specific module
$ cargo expand --test my_module
```
