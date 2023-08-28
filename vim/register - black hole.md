parent: [[+ vim]]

cut inside word, sending to void: `"_diw`

or

```vim
:normal "_diw
```

- sends text that would usually be sent to the [[register - unnamed|unnamed register]] to the void, preventing the unnamed register from being updated

## Related

- [[dev null|/dev/null]]