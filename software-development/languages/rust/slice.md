parent: [[+ rust]]

- slices are dynamically sized views into continuous sequences, `[T]`
    * dynamic, because the length of a slice may change, whereas arrays are
        fixed in length
    * contiguous means that every item in the sequence is the same distance from
        the next item
- a slice contains 2 pieces of information:
  * a pointer to the memory location - i.e. it is a reference
  * the number of elements in the slice, or length
- because slices store both the reference and a length, they occupy twice the
    amount of space as other references

    ```rust
    use std::mem;
    use std::rc::Rc;

    fn main() {
        let u8_ref_size = std::mem::size_of::<&u8>();

        // u8 slice
        assert_eq!(2 * u8_ref_size, mem::size_of::<&[u8]>());
        // u8 raw pointer
        assert_eq!(2 * u8_ref_size, mem::size_of::<*const [u8]>());
        // Boxed u8
        assert_eq!(2 * u8_ref_size, mem::size_of::<Box<[u8]>>());
        // ref-counted u8
        assert_eq!(2 * u8_ref_size, mem::size_of::<Rc<[u8]>>());
    }
    ```
- slices are either:
  * shared, i.e. `&[T]`
  * mutable, i.e. `&mut [T]`
    + a mutable slice can mutate the referenced memory's contents

        ```rust
        let mut xs = [1,2,3];
        let xs = &mut xs[..]; // full slice of xs
        xs[1] = 42;

        assert_eq!(xs, &[1,42,3]);
        ```
- slices are one of a few _dynamically sized types_ - see [[Sized]]

# links and resources

- https://doc.rust-lang.org/std/primitive.slice.html
- https://doc.rust-lang.org/1.74.0/reference/dynamically-sized-types.html
