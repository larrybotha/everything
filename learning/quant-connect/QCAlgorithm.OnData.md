---
aliaes:
  - data event
---

parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Minute)

    def OnData(self, data):
        self.Debug(data["SPY"].Price)
```

The `QcAlgorithm.Ondata` method in an algorithm, which allows for handling time
slice events - a time slice is the _end_ time of a unit of the resolution
subscribed to for an equity at [[QCAlgorithm.Initialize]].

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

- https://www.lean.io/docs/v2/lean-engine/class-reference/classQuantConnect_1_1Algorithm_1_1QCAlgorithm.html#a5c061402f5e7fa7ff52209404017c8c3
- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#OnData-header
- [Slice](https://www.lean.io/docs/v2/lean-engine/class-reference/classQuantConnect_1_1Data_1_1Slice.html
