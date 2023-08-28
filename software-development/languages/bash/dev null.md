---
aliases:
	- /dev/null
---

parent: [[+ bash]] 

```shell
# don't print pwd to screen
$ pwd >/dev/null

# send stdout and stderr from foo to void
$ foo >/dev/null 2>&1
# [1] [    2   ] [3]
# 1 - for the command "foo"
# 2 - redirect stdout to /dev/null
# 3 - and redirect stderr to wherever stdout is being redirected
```

- prevent errors from being rendered to the screen 
- test a command while silencing the output
- send unneeded data to the void 

## Related

- [[bash redirects]]

## Links and resources
- https://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/