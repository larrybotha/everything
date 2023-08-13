parent: [[+ vim]]

- list all key mappings:
```
:[n|v|i|o]map
```
- list key mappings for a specific key combination:
```
:[n|v|i|o]map [key-combination]

" e.g. what is <leader>b bound to in normal mode?
:nmap <leader>b
```
- list key mappings with the location where they're defined
```
:verbose [n|v|i|o]map [key-combination]	
```