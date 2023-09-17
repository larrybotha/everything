---
aliases:
  - true
  - false
---
parent: [[+ The Lambda Calculus]]

```
def true  = first
def false = second
```

## derivation

We have the ternary operator in many languages:

```
condition ? x : y
```

If we know the values of `x` and `y`, from [[cond - the lambda calculus|cond]] we have

```
   ((cond x) y)
=> ((λe1.λe2.λc.((c e1) e2) x) y)
=> (λe2.λc.((c x) e2) y)
=> λc.((c x) y)
```

We need to solve for `c`.

Given the ternary operator above, which condition satisfies the expression such that it resolves to `x`?

That condition / function turns out to be [[first - the lambda calculus|first]]:

```
   (λc.((c x) y) first)
=> ((first x) y)
=> x
```

Thus, [[first - the lambda calculus|first]] can be used to represent `true`

Similarly, for the expression to resolve to `y`, we can use [[second - the lambda calculus|second]]:

```
   (λc.((c x) y) second)
=> ((second x) y)
=> y
```

and we can use [[second - the lambda calculus|second]] to represent `false`