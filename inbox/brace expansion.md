Parent: [[+ bash]]

```shell
touch {foo,bar,baz}.md

# equivalent to
touch foo.md bar.md baz.md

# sequence expansion
for i in {1..10} {a..f}; do
  sleep 1
  echo $i
done
```

- makes commands more concise
- is the first substitution that bash performs when transforming commands- see [[bash expansion]]
- brace expansion in bash happens *before* [[parameter expansion]] - i.e. parameters can't be used inside brace expansion, because they'll only be expanded after the braces are expanded:

```shell
# won't expand in bash; will in zsh
$ n=5; echo {1..$n}
```

   Because of this, building arrays from brace expansion with sizes known at runtime in bash is difficult

```shell
# won't work in bash
for i in {1..$n}; do
```
   
   For integer iteration, prefer an arithmetic loop:

```shell
for ((i=1; i<=n; i++)); do
  # ...
done
```


## links and resources

- https://mywiki.wooledge.org/BraceExpansion