A data type whose concrete data structure is not defined in an interface, i.e. it is a firm of information hiding

e.g. in OOP private fields are opaque data types, in contrast to the public fields, which are transparent data types

Opaque data types may only be interacted with via subroutines, not directly. It is useful for hiding implementation details, which means the interface to the type containing the opaque data type can remain the same while the implementation can be updated freely

## links and resources

- https://en.wikipedia.org/wiki/Opaque_data_type
- https://chunminchang.github.io/blog/blog/post/opaque-or-transparent-data-type-in-a-rust-library