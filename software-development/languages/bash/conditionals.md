parent: [[+ bash]]

```shell
x="foo"
y="bar baz"

# '[' is called 'test', and is a 
# command. i.e. the space is required
# It accepts 4 arguments, 
# including ']' as the final argument
if [ "$x" = "$y" ]; 
then ... 
else ... 
fi

# 'if' is optional
[ "$x" = "$y" ] # => false

# quotes are required, otherwise words are treated as separate args 
[ $x = $y ] 
bash: [: too many arguments
# expands to 5 arguments:
# [ foo = bar baz ]

# equivalent to using 'test'
[ -f "test.png" ] # false
test -f "test.png" # false

# '[[' is a keyword, and has more
# features
# e.g. arguments are parsed before they are expanded
[[ $x = $y ]] # valid - evaluates to false

# pattern matching
[[ "test.png" = *.png ]] # globs

# =, !=, >, and < treat their arguments as strings
# -ne (not equal), -lt (less than), -gt, -le (less than or equal to), or -ge treat their arguments as numbers
[[ "314" < "42" ]] # true
[[ 314 -lt 42 ]] # false
```

- use `[[` in environments where you know bash will be used, otherwise use `[`
- don't use `[` with `-a` or `-o` - use multiple commands instead

## Links and resources

https://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29