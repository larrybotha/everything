---
aliases:
  - reduce
---

parent: [[+ The Lambda Calculus]]

```
def reduce =
```

## derivation

We cannot define a function in terms of itself, because [[β reduction|normal order reduction]] requires that we replace names in expressions before evaluating them, resulting in non-terminating definitions

e.g.

```
# for some recursive function f
def foo x y = cond z (foo x y)

# when writing f, it contains itself
# as a named expression, and we must
# replace it with its definition
   λx.λy(cond z (foo x y)) a b
=> λx.λy(cond z (
     # replace f with is definition
     λx.λy(
       cond z (foo x1 y1)) x y
     )) a b
=> λx.λy(cond z (
     λx.λy(
       cond z (
         # and again
         cond z (foo x2 y2)) x y
       )) a' b'
     )) a b
# and so on
=> ...
```

So functions that are defined in terms of themselves are non-terminating

How do we deal with this? We need to delay the calling of the function to prevent having to expand its definition. 

Application of a given function can be rewritten by raising the function as an argument to a higher order function:

```
def bar = λx.λy.(...)

# create a HOF
def quux = λf.λx.λy.((f x) y)

# apply bar via abstraction
(((quux bar) x) y)
```

By abstracting the function application to a higher order function we eliminate the function referring to itself, suggesting that we can use a HOF to assist in defining the recursive function:

```
def foo_hof f x y = 
	cond do_z (f x y)

def foo = foo_hof foo_hof
```

Expanding this we get

```
   (λf.λx.λy.(
     (cond do_z (f x y)) foo_hof
=> λx.λy.
     cond do_z (foo_hof x y)
     #                  ↑
     #                oops!
```

With this definition of `foo_hof` the internal function call is missing an argument. 

To resolve this, the internal function must accept itself as an argument:

```
def foo_hof f x y =
	cond do_z (f f x y)

def foo = foo_hof foo_hof
```

This evaluates to

```
   (λf.λx.λy.(
     (cond do_z (f f x y)) foo_hof
=> λx.λy.
     cond do_z (foo_hof foo_hof x y)
```

The definition of `foo_hof` doesn't contain any named values, so we don't strictly need to replace it with its definition