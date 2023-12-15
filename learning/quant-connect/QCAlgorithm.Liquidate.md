parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

    def OnData(self, data):
        # ...

        self.Liquidate(self.spy.Symbol)
```

- liquidates all holdings and cancels any open orders for a given symbol
- used in tandem with [[QCAlgorithm.SetHoldings]]


## links and resources

- https://www.quantconnect.com/learning/task/130/Using-our-Signal-to-Flip
- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#Liquidate-header
