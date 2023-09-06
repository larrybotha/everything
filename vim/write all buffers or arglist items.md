parent: [[+ vim]]

```vim
" write all items in buffer list
:wall

" write all items in arglist
:argdo write

" write current file, go to next in arglist. Useful in macros operating on arglist 
:wnext
" or
:write
:next
```

## Related
- [[arguments list]]
- [[argdo]]