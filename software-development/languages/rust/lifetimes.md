parent: [[+ rust]]

- lifetime parameters in structs indicate to the compiler which values in the
  struct must have lifetimes _at least_ as long as the lifetime of the struct

      ```
      // field x's value must live at least as long as Foo
      struct Foo<'a> {
      	x: &'a Bar
      }

         Foo { x }

            ├―――――――――――――――――――――――――――――――――――――――――――▶

      	 x

      1: ├―――――――――――――――――――――――――――――――――――――――――――――――――――――▶
      2:         ├―――――――――――――――――――――▶
      3: ├―――――――――――――――――――――――――――――▶
      ```

      1. safe: if x is dropped, Foo will already have been dropped, and all
         references removed
      2. impossible: Foo can't be instantiated without x existing
      3. dangling reference: if x is dropped before Foo is dropped, we'll have a
         dangling reference - a reference to a value that no longer exists
