parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

        # ...

        # if we had indicators, we'd want them to be warmed up with market data
        # before we begin using them
        self.SetWarmUp(50)

    def OnData(self, data):
        # don't do anything until warm
        if self.IsWarmingUp:
            return
```

- will run the algorithm for x units of the specified resolution before the
    start date
- useful for populating indicators with data before the algorithm begins
    executing trades
- a `IsWarmingUp` attribute is available on the instance - don't place trades
    until warm

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#SetWarmUp-header
- https://www.quantconnect.com/learning/task/129/Preparing-an-Indicator-for-Testing
- https://www.quantconnect.com/docs/v2/writing-algorithms/historical-data/warm-up-periods
