---
tags:
  - resource/video
---

Link: https://www.youtube.com/watch?v=y5utZCeHys0

- level 1
    * errors in go are interfaces that have a single method called `Error` which
        returns a string
    * errors can be compared against `nil`, because errors are interfaces, and
        interfaces can be `nil` - thus, any value can be compared against `nil`, and
        if we don't have `nil`, something went wrong
    * `log.Fatal` is often used to print errors and then exit the process
- level 2
    * `errors.New()` is used to create new errors
    * `fmt.ErrorF()` is an alternative way to create errors using formatted strings
- level 3
    * one could naively check the value of an error to determine if you're getting
        the error you expect, but it's more scalable to evaluate the _type_ of errors
    * an alternative is to define the error as a variable, and evaluate against
        that variable elsewhere in the code
    * it' s a convention in Go to prefix errors with `Err`
    * the problem with this approach is that we're unable to specify dynamic values
        in errors
- level 4
    * custom errors are a more flexible way of creating errors, and they are
        created by:
        + defining a struct, conventially _suffixed_ with `Error`
        + implementing `Error`, returning a string, which means the struct has
            implemented the `error` interface
    * building on this, we can determine if a specific error is the type we expect
        by:
        + defining a `var` of the error type
        + passing the error and a reference to the variable to `errors.As`
    * once the type of an error is confirmed using`errors.As`, data from that type
        of error can be extracted from the error
- level 5
    * when formatting an error, specifying `%w` in the format string will result
        in a wrapped error being returned, similar to Python's
        `raise MyException('foo') from e`
    * `errors.Unwrap` then allows for unwrapping an error to access wrapped errors
    * the demo in the video describes wrapping an error that contains metadata
        about the specific loation of an error which is useful when unwrapping
        the error laater for user feedback









