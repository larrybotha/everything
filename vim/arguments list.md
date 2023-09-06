parent: [[+ vim]]

```vim
" view the args list 
:args

" populate the args list
:args index.html app.ts
:args *.*
:args *.py
:args **/*.*
:args **/*.rs **/*.json
:args `cat files.txt`

" navigate
:first
:last
:next
:prev
```

- allows for storing a list of files that can be navigated and operated on from Ex mode

## Related

- [[argdo]]

