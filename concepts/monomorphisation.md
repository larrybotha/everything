The generating of specialised functions at compile-time for languages that make
use of generics in functions

e.g. in Rust, for every implementation of a generic function, the compiler will
generate code for that function with its body containing the concrete types, as
opposed to evaluating at runtime which paths to take for specific types. This
improves performance at runtime while making it simpler for the developer to
write maintainable code.
