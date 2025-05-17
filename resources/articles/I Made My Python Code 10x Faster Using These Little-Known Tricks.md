---
tags:
  - resource/article
---

Link: https://archive.is/pMQcD

## takeways

- use `enumerate(...)` instead of `range(len, ...)`
- use Python's `array` or `deque` for working with large lists of primitive types
- use `functools.lru_cache` for pure functions
- use `line_profiler` for profiling

    First:

    `pip install line_profiler`

    then:

    ```python
    @profile
    def my_func():
    ...

    then:

    ```shell
    kernprof -l my_script.py
    python -m line_profiler my_script.py.lprof
    ```
- pre-allocate large lists rather than appending to them:

    ```python
    # Slow
    result = []
    for i in range(1000000):
        result.append(i)

    # Faster
    result = [None] * 1000000
    for i in range(1000000):
        result[i] = i
    ```
- use [`msgspec.Struct`](https://jcristharif.com/msgspec/structs.html)
    for structured data  types - it's faster



