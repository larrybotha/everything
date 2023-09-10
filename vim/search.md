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

" match words starting with 'foo'
/\<foo

" match words ending in 'foo'
/foo\>

" search by word boundaries
" e.g. match only on the word 'the' - not 'these', 'them ', etc.
" can also be used outside of verymagic search by escaping with backslashes 
/\v<the>

" use verynomagic search - i.e. verbatim search
" points are treated literally, not as regex characters 
" equivalent to /a\.k\.a
/\Va.k.a

" match the end of the line 
/\_$

" match within a search, starting from the new search value- \zs
" e.g. match 'bar' in 'foo bar'
" similar to regex positive lookbehind
/foo\s\zsbar

" match within a search, ending at the new search value - \ze
" e.g. match everything up to 'bar' in lines containing 'foo'
" similar to regex positive lookahead
/.*foo.*\zsbar

" combining both, e.g. to match everything between quotes
/\v"\zs[^"]+\ze

" position cursor at end of match
" Useful for repeatable actions at the end of words or matches
" e.g. updating foo => foobar and foos => foobars with the same action
/foo/e<CR>
```

- in forward searches, using `/`, matching a literal `/` requires escaping the character, e.g. `/https:\/\/example.com?q=foo`
- in backward searches, using `?`, matching a literal `?` requires escaping the character, e.g. `?https://example.com\?q=foo`
- the last search term can be modified by first getting it, using, `/`, and then adding to it. e.g.
	```vim
	" match foo
	/foo<CR>

	" modify last search, placing the cursor at the end of the match
	//e<CR>
	```

	Notice how there's no need to escape `/`

## Related

- [[improved dot formula]]