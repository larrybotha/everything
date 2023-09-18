---
aliases:
  - or
---

```
def or = λx.λy.((x true) y)
```

## derivation

For `or` we have

|x|y|x or y|
|---|---|---|
|T|T|T|
|T|F|T|
|F|T|T|
|F|F|F|

i.e. `x ? true : y`

- if the left is `true`, choose `true`
- otherwise choose the right

Therefore, using [[cond - the lambda calculus|cond]], we have:

```
λx.λy.(((cond true) y) x)
```

After reducing and simplifying:

```
   λx.λy.(((cond true) y) x)
=> λx.λy.(((
     λe1.λe2.λc((c e1) e2)
     true) y) x)
=> λx.λy.((x true) y)
```

## assertions

`true or true == true`

```
   ((or true) true)
=> ((λx.λy.((x true) y) true) true)
=> ((true true) true)
=> ((first true) true)
=> true
```
---

`true or false == true`

```
   ((or true) false)
=> ((λx.λy.((x true) y) true) false)
=> ((true true) false)
=> ((first true) false)
=> true
```
---

`false or true == true`

```
   ((or false) true)
=> ((λx.λy.((x true) y) false) true)
=> ((false true) true)
=> ((second true) true)
=> true
```
---

`false or false == false`

```
   ((or false) false)
=> ((λx.λy.((x true) y) false) false)
=> ((false true) false)
=> ((second true) false)
=> false
```