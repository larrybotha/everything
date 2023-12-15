parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

        self.spyMomentum = self.MOMP(self.spy.Symbol, 14, Resolution.Daily)

        # ensure our indicator is warmed up
        self.SetWarmUp(14)

    def OnData(self, data):
        # make sure our indicator is ready
        if not (self.spyMomentum or self.spyMomentum.IsReady):
            return

        if self.spyMomentum.Current.Value > 0:
            # ...
            self.Debug("SPY is up")
```

- creates a momentum percent indicator on a ticker
- value can be read using `indicator.Current.Value`
- indicators should be validated before being used

## related

- [[QCAlgorithm.SetWarmUp]]

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#MOMP-header
- https://www.quantconnect.com/learning/task/129/Preparing-an-Indicator-for-Testing
