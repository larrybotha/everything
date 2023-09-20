---
aliases:
  - pred
---
parent: [[+ The Lambda Calculus]]

```
def pred = 
	λn.(((iszero n) zero) (n second))
```

The predecessor of a natural number
## derivation 

We need to define a function which, given a natural number:

- returns the value preceding the current value if the current value is not zero
- otherwise returns zero

Each non-zero natural number defined using [[succ - the lambda calculus|succ]] contains the preceding number. How can we resolve to the contained number?

How about applying the outer number to [[second - the lambda calculus|second]]:

```
   (λs.((s false) n) second)
=> ((second false) n)
=> n
```

That works! How about zero:

```
   (zero second)
=> (id false)
=> false
```

This resolves to a value which is not a natural number.

Instead, we can use [[iszero - the lambda calculus|iszero]] with [[cond - the lambda calculus|cond]] to evaluate the current number:

-  if it is zero, return zero
- otherwise, use `second` to return the previous number

```
   λn.(((cond zero) (n second)) 
     (iszero n))
=> λn.(((iszero n) zero) (n second))
```

An alternative way to handle zero is by working with an undefined value, but we won't do that here