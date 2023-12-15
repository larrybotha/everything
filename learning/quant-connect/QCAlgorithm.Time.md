parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...

    def OnData(self, data):
        # only allow trades to be placad on Wednesdays
        if self.Time.weekday() != 3:
            return
```

- `self.Time` is a datetime object for the current date and time of the event
- trades placed using `Resolution.Daily` are only evaluated after the market is
    closed, and will be available to be filled the next day

## links and resources

- https://www.quantconnect.com/learning/task/131/Time-Our-Market-Moves
- https://www.quantconnect.com/docs/v2/writing-algorithms/key-concepts/time-modeling/periods
