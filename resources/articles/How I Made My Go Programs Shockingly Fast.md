---
tags:
  - resource/article
---

Link: https://archive.is/43FoV

## takeaways

- where many objects are being created and discarded quickly, consider
    using `sync.Pool` for a short-lived cache:

    ```go
    var bufPool = sync.Pool{
        New: func() interface{} {
            return new(bytes.Buffer)
        },
    }

    func handler(w http.ResponseWriter, r *http.Request) {
     buf := bufPool.Get().(*bytes.Buffer)
     defer bufPool.Put(buf)
     buf.Reset()
     // Use buf...
    }
    ```
- as in [[I Made My Python Code 10x Faster Using These Little-Known Tricks]],
    pre-allocate slices if you know the size, rather than blindly
    appending
- avoid `interface{}` in favour of using concrete types, unless dealing with
    something like dynamic json
- use `pprof` to profile Go code:

    ```go
        import _ "net/http/pprof"
    import "net/http"

    func main() {
     go http.ListenAndServe("localhost:6060", nil)
    }
    ```

    then:

    ```shell
    # browser
    open http://localhost:6060/debug/pprof/

    # or, cli
    go tool pprof http://localhost:6060/debug/pprof/profile
    ```
- prefer `range` over manually indexing values in a for-loop
- prefer `bytes.Buffer` or `strings.Builder` over `+` for building
    strings
- `defer` has overhead - if you looping over a ton of items, such as
    opening files, it can improve performance to call `f.Close`

