parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.iwm = self.AddEquity("IWM", Resolution.Daily)

        self.SetBenchMark("SPY")
```

- sets the benchmark for statistics of the algorithm against the given ticker or
  symbol
- has a number of other overrides, beyond providing only the ticker, including a
  callback

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#SetBenchmark-header
