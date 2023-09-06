parent: [[+ vim]]

```vim
" search 'foo' in the current buffer
" results depend on ignorecase / smartcase options
/foo

" search 'foo' case-insensitive
/foo\c

" search 'foo' case-sensitive
/foo\C

" use very magic search - Perl / Python / Ruby flavoured regex
/\vfo{2}

" search by word boundaries
" e.g. match only on the word 'the' - not 'these', 'them ', etc.
" can also be used outside of verymagic search by escaping with backslashes 
/\v<the>

" use verynomagic search - i.e. verbatim search
" points are treated literally, not as regex characters 
" equivalent to /a\.k\.a
/\Va.k.a


```