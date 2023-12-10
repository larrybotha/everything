---
aliaes:
  - data event
---

parent: [[+ quant connect]]

The `QcAlgorithm.Ondata` method in an algorithm, which allows for handling time
slice events - a time slice is the _end_ time of a unit of the resolution
subscribed to for an equity at [[algorithm-initialization|initialization]].

- buy shares of a given symbol:

    ```python
    self.MarketOrder(
      symbol: Symbol,
      quantity: int,
    )
    ```

    This function executes synchronously - no need to evaluate order events
- set a stop order to exit a position at a given market price:

    ```python
    self.StopMarketOrder(
      symbol: Symbol,
      quantity: int,
      price: int,
    )
    ```

## links and resources

-
