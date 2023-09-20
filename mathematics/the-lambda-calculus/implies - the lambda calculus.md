---
aliases:
  - implies
---

```
def implies = λx.λy.((x y) true)
# or
def implies x y = 
	if x 
	then y 
	else true
```

## derivation

For `implies` we have

|x|y|x => y|
|---|---|---|
|T|T|T|
|T|F|F|
|F|T|T|
|F|F|T|

i.e. `x ? y : true`

- if the left is `true`, choose the right
- otherwise `true`

Therefore, using [[cond - the lambda calculus|cond]], we have:

```
λx.λy.(((cond y) true) x)
```

Simplifying and reducing:

```
   (λx.λy.(((cond y) true) x))
=> (λx.λy.((x y) true))
```

## assertions

`true implies true == false`

```
   implies true true
=> ((x y) true) true true
=> ((true true) true)
=> first true true
=> true
```

---
`true implies false == false`

```
   implies true false
=> ((x y) true) true false
=> ((true false) true)
=> first false true
=> false
```

---
`false implies true == true`

```
   implies false true
=> ((x y) true) false true
=> ((false true) true)
=> second true true
=> true
```

---
`false implies false == true`

```
   implies false false
=> ((x y) true) false false
=> ((false false) true)
=> second false true
=> true
```
