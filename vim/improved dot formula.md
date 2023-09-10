parent: [[+ vim]]

Given:

```python
class XmlDoc:
	"""
	XmlDoc
	"""
	pass

class XhtmlDoc(XmlDoc):
	"""
	XhtmlDoc
	"""
	pass


```

If we wanted to upper case `Xhtml` and `Xml`

```vim
" match on chars, using verymagic, and case-sensitive
/\vX(ht)?ml\C

" uppercase next match
gUgn

" repeat without having to explicitly move to next match
.
.
.
```

- `gn` behaves on search matches in two ways:
	- if in operator-pending mode, apply that operation to the next match
	- otherwise, visually select up until the next match
- in operator-pending mode, there's no need to press `n` to get to the next match - it takes you there, and applies the operation, meaning you can mitigate mashing `n.` repeatedly
- something to be careful of: `n.` allows for inspecting the text before the change, whereas `gn` will replace before you may see what's being replaced