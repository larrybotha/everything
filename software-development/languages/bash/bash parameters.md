parent: [[+ bash]]

- parameters are expanded by prefixing them with a `$`
- always double-quote parameter expansions
- parameter expansions are also known as substitutions
## variables

Variables are parameters that are denoted by a name

```shell
# no spaces
$ foo="bar"

# the following is a command that is
# passed an equal sign and text
$ foo = "bar"

# parameter expansion tells bash that
# we want to access the contents of
# a variable
$ echo "$foo"

# always quote variable expression
$ file="my file.png"
$ rm $file 
rm: my: No such file or directory
rm: file.png: No such file or directory

# the above fails because it expands
# s.t. rm receives 2 arguments:
# $ rm my file.png
```

## special parameters

Parameters that *aren't* variables are called *special parameters*

```shell 
# 0, 1, 2, #, *, ?, !, $, _ are
# all special parameters
# we use parameter expansion to
# access their contents 
$ echo "$0" # name or path of script
$ echo "$?" # last command's exit code
$ echo "$1" # first positional param 
$ echo "$*" # all positional params, expands to string 
$ echo "$@" # all positional params, expands to list
$ echo "$#" # expands to number of positional arguments
$ echo "$$" # expands to PIS of current shell 
```

## Links and resources

https://mywiki.wooledge.org/BashGuide/Parameters