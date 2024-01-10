parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

    def OnData(self, data):
        if not self.Portfolio.Invested:
            # place a market order to purchase 75% of the available cash in SPY
            self.SetHoldings(self.spy.Symbol, 0.75)
```

- liquidates all holdings and cancels any open orders for a given symbol
- used in tandem with [[QCAlgorithm.Liquidate]]

## links and resources

- https://www.quantconnect.com/learning/task/130/Using-our-Signal-to-Flip
- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#SetHoldings-header
