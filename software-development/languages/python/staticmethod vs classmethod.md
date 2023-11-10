parent: [[+ python]]

| feature                    | `@classmethod` | `@staticmethod` |
| -------------------------- | -------------- | --------------- |
| overridable by subclasses  | yes            | no              |
| access to class attributes | yes            | no              |
| can be called on instance  | yes            | yes             |

- `@classmethod` and `@staticmethod` functions can be called either directly
  from the class, or from instances - instance methods are only callable in the
  context of an instance

  - methods are similar to Rust in this way - one can either call the method
    directly, or pass the instance into the function defined on the class:

    ```python
    class Foo:
    	def __init__(self, value):
    		self._value = value

    	def instance_method(self):
    		return self._value

    foo = Foo("x")

    assert (
    		foo.instance_method() == Foo.instance_method(foo),
    		"not equal"
    )
    ```

- `@staticmethod` is a way for encapsulating functions inside classes without
  giving them access to any of the class's attributes
- `@classmethod` can be called either from the class or on instances
