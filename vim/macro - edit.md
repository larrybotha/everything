parent: [[+ vim]]

```vim
" record macro into register 'a'
qa

" perform keystrokes...

" paste macro 'a' on next line
:put a

" edit macro text...

" yank text back into register 'a', excluding new line
"ay$
```

