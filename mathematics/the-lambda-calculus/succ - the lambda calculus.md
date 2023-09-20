---
aliases:
  - succ
---
parent: [[+ The Lambda Calculus]]

```
def succ = λn.λs.((s false) n)
#         [1] [2]
# 1 - number to apply succ to
# 2 - original number
```

Defines a successor function for natural numbers

i.e. we have [[zero - the lambda calculus|zero]], so the successor of zero is one, the successor of one is two, etc.

```
def one =  (succ zero)
		=> (λn.λs.((s false) n) zero)
		=> λs.((s false) zero)

def two =  (succ one)
		=> (λn.λs.((s false) n) one)
		=> λs.((s false) one)
		=> λs.((s false) 
			λs.((s false) zero))
		# which is also
		=> (succ (succ zero))

def three =  (succ two)
		  => (λn.λs.((s false) n) two)
		  => λs.((s false) two)
	      => λs.((s false) 
	           λs.((s false) 
			     λs.((s false) zero)))

# etc.
```