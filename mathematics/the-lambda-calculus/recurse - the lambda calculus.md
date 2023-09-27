---
aliases:
  - recurse
---

parent: [[+ The Lambda Calculus]]

```
def recurse =
```

## derivation

We cannot define a function in terms of itself, because [[β reduction|normal order reduction]] requires that we replace names in expressions before evaluating them. With functions that refer to themselves this results in non-terminating definitions

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

With this definition of `foo_hof` the internal function call is missing an argument - the function that needs to be called inside `foo_hof`. 

To resolve this, the internal function must also accept a function as an argument:

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

The definition of `foo_hof` doesn't contain any named values - specifically references to itself - so we don't strictly need to replace it with its definition

For clarity, let's do a specific implementation. We can define a recursive `add` function for natural numbers using this new knowledge:

- `add` must accept two arguments, and return the sum
- for it to be recursive, it needs to be defined in terms of a higher order function
- that higher order function must itself be responsible for two things:
	- calculating the sum 
	- recursively calling some addition function until the sum is calculated
- the HOF must:
	- accept a function
	- accept the arguments to add together
	- terminate on some condition
	- call the function passed in, passing that function:
		- a copy of that same function
		- the augmented arguments that will be summed or evaluated on the next iteration
- for natural numbers, the sum of two numbers can be calculated recursively by incrementing the first number, while decrementing the second number, until the second number is zero

With this information, we can define the higher order function as such:

```
def add_hof f x y =
	if iszero y
	then x
	else f f (succ x) (pred y)
```

Which function can we pass into `add_hof` so that it can recursively perform addition? 

Well... if we pass it to itself, we get a new partially applied function that accepts 2 arguments:

```
   def add x y = add_hof add_hof x y
=> λx.λy.
	 if iszero y
	 then x
	 else add_hof (
		add_hof (succ x) (pred y)
	 )
```

e.g.

```
   add one two 
=>  if iszero two
	then one
	else add_hof (
	  add_hof (succ one) (pred two)
	)
=>  if iszero one
	then two
	else add_hof (
	  add_hof (succ two) (pred one)
	)
=>  if iszero zero
	then three 
	else add_hof (
	  add_hof (succ three) (pred zero)
	)
=> three 
```

Now, we need a way to generalise this so that we can define recursive functions given other functions that are:

- higher-order
- not self-referencing
- recursive if passed into themselves

If we take a look at [[self-application - the lambda calculus|self_apply]], it appears to do something similar to what we've been doing with these higher order functions - the inner function applications in our HOFs always self-apply and then accept subsequent arguments, as does the definition of our partially applied recursive function

WIP

We can delay application of [[self-application - the lambda calculus|self_apply]] by placing it in a HOF:

```
def self_apply_hof f = λs.(s s) f
```

Given a HOF `h`, we need a function `recurse` such that it produces a recursive function `f`

We know that `f` looks something like the following:

```
def f x y z... = h h x y z...
```

and we need `recurse` such that it produces `f`

```
def recurse h = ...?
```