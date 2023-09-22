---
aliases:
  - equiv
---
parent: [[+ The Lambda Calculus]]

```
def equiv = λx.λy.((x (and x y)) (not y))
# or
def equiv x y = 
	if x
	then and x y
	else not y
```

## derivation

For `equiv` we have

|x|y|x <=> y|
|---|---|---|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|T|

i.e. `x ? x and y : not y`

- if the left is `true`, then `x` and `y` need to both be `true` for a `true` outcome
- otherwise select the inverse of `y`

Therefore, using [[cond - the lambda calculus|cond]], we have:

```
λx.λy.(((cond (x and y)) (not y)) x)
```

Simplifying and reducing:

```
   (λx.λy.(((cond (and x y)) (not y)) x))
=> (λx.λy.((x (and x y)) (not y)))
```

## assertions

`true equiv true == true`

```
   equiv true true
=> ((x (and x y)) (not y)) true true
=> true (and true true) (not true)
=> first true false
=> true
```

---
`true equiv false == false`

```
   equiv true false
=> ((x (and x y)) (not y)) true false
=> true (and true false) (not false)
=> first false true
=> false
```

---
`false equiv true == false`

```
   equiv false true
=> ((x (and x y)) (not y)) false true
=> false (and false true) (not true)
=> second false false
=> false
```

---
`false equiv false == true`

```
   equiv false false
=> ((x (and x y)) (not y)) false false
=> false (and false false) (not false)
=> second false true
=> true
```

## exercises

Q: Show that the following are equivalent:

```
 i) `equiv`
ii) `λx.λy.(and (implies x y) (implies y x))
```

A:
We need the two arguments to `and` to both be `true` given `x` and `y`

From the truth table for [[implies - the lambda calculus|implies]] we know that:

- when the two values are the same, the outcome is always `true`
- when the two values are different, the outcome is sometimes `true`

When the values passed to `and` are different, it will always return `false`, otherwise `true`

Therefore for all values of `x` and `y` the two statements are equivalent