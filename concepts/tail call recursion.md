In programming, a procedure that calls itself as the final action of the procedure

## proper tail recursion

Tail recursion where no additional stack frames are created for each successive call. This is dependent on the implementation of the compiler / interpreter

i.e. the currently executing function doesn't need to wait for the result of the recursive call before it can return a value

e.g.

```lua
-- recursive, but not tail-recursive,
-- the product of each call depends on the subroutine's result before calculating,
-- pushing each call onto the stack 
function factorial(n)
	if n == 0 then
		return 1
	else
		return n * factorial(n - 1)
	end
end

-- every call has all the information
-- it needs - no pushing onto the
-- stack
function factorial_proper(n, acc)
	acc = acc or 1
	
	if n == 0 then
		return acc
	else
		return factorial_proper(
			n - 1, acc * n
		)
	end
end
```

e.g. Lua supports proper tail recursion, and the following will not result in a stack overflow:

```lua
function foo(n)
	if n > 0 then 
		return foo(n - 1) 
	end
end
```

## tail call optimisation / tail call elimination

Whether a compiler or interpreter will push tail calls onto the stack or not

Python does not perform tail call optimisation, so whether using recursion with our without tail calls the stack will always be pushed to

Lua, however, will optimise tail calls

## trampoline

A mechanism for implementing tail-recursive functions in languages that do not support tail call optimisation, resulting in constant stack space usage

1. define a trampoline function that accepts an argument which is either a function with arity 0, or a value
	1. in a loop, call the function, reassigning the trampoline's argument to the result, until it returns something other than a function
	2. return that result
2. define a recursive function that has a base case to return the computed value, or a closure with arity 0 that returns the recursive call
3. execute the recursive function inside a closure, passed to the trampoline