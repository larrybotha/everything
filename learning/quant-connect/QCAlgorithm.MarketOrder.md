parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

    def OnData(self, data):
        self.MarketOrder(self.spy.Symbol, 100)
```

- sends a market order and waits for it to be filled
- the returned object has an `OrderId` attribute that can be compared against the
    object the event handler receives
- executes synchronously - no need to evaluate order events


## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#MarketOrder-header
