Link: https://preslav.me/2023/04/14/golang-error-handling-is-a-form-of-storytelling/

- Go has a `fmt.Errorf` function which, when used with its `%w` flag, wraps errors in a similar way to Python's `raise e2 from e1` strategy
- phrase errors in Go with respect to what you were trying to do, not what went wrong
- unlike Python, unhandled errors in Go will crash the entire application

## related

- [[+ golang|Golang]]