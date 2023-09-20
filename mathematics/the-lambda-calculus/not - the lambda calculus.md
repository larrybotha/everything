---
aliases:
  - not
---
parent: [[+ The Lambda Calculus]]

```
def not = λx.((x false) true)
```

## derivation

`not` has the following truth table:

|x|not x|
|---|---|
|T|F|
|F|T|

which can be modelled as

`x ? false : true`

`not` is unary, so our function needs to accept a single parameter.

Thus, we have:

```
   (λx.((cond false) true) x)
=> (λx.((
     λe1.λe2.λc.(
       (c e1) e2) false) true
     ) x
   )
=> (λx.(
       λc.((c false) true)
     ) x
   )
=> ((x false) true)
```

## assertions

`not true == false`

```
   (not true)
=> (λx.((x false) true) true)
=> ((true false) true)
=> ((first false) true)
=> false
```

---

`not false == true`

```
   (not false)
=> (λx.((x false) true) false)
=> ((false false) true)
=> ((second false) true)
=> true
```

## related

- [[booleans - the lambda calculus]]
- [[cond - the lambda calculus|cond]]