parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

    def OnData(self, data):
        self.marketOrder = self.MarketOrder(self.spy.Symbol, 100)

    def OnOrderEvent(self, orderEvent):
        if orderEvent.OrderId == self.marketOrder.OrderId:
            self.Debug("order filled")
```

- allows for handling fills of orders

## related

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#OnOrderEvent-header
