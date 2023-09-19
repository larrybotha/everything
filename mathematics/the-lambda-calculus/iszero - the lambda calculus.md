---
aliases:
  - iszero
---
parent: [[+ The Lambda Calculus]]

```
def iszero = λn.(n first)
```
## derivation 

Given a natural number, we need some way to obtain a boolean value indicating whether that value is zero or not.

Non-zero naturals are represented by [[succ - the lambda calculus|succ]] applied to the previous number. Each number takes a single argument:
```
def nat_x = λs.((s false) n)
```

[[zero - the lambda calculus|zero]] is equivalent to identity

```
def zero = id
		 = λx.x
```

Both of these are functions that accept a single argument.

Is there something that either of these functions can be applied to that will indicate whether the number being operated on is zero or not?

How about [[first - the lambda calculus|first]]?

```
   (zero first)
=> (id true)
=> true

   (nat_x first)
=> (λs.((s false) n) first)
=> ((first false) n)
=> false
```

Looks good! If we apply a natural number to `first`,  it resolves to a boolean indicating whether it's zero or nonzero

Therefore, we have a function which takes a single argument, a natural number, and applies it to `first`:

```
def iszero = λn.(n first)
```