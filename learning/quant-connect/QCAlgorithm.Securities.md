parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Minute)

    def OnData(self, data):
        self.Debug(self.Securities(self.spy.Symbol].Price))
        self.Debug(self.Securities(self.spy.Symbol].Close))
        self.Debug(self.Securities(self.spy.Symbol].High))
        self.Debug(self.Securities(self.spy.Symbol].Low))
        self.Debug(self.Securities(self.spy.Symbol].Volume))
        self.Debug(self.Securities(self.spy.Symbol].OpenInterest))
```

- get a `SecuritiesManager` object

## links and resources

- [Securities](https://www.lean.io/docs/v2/lean-engine/class-reference/classQuantConnect_1_1Securities_1_1SecurityManager.html)
- [Security](https://www.lean.io/docs/v2/lean-engine/class-reference/classQuantConnect_1_1Securities_1_1Security.html)
