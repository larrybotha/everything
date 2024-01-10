parent: [[+ quant connect]]

```python
class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

    def OnData(self, data):
        self.MarketOrder(self.spy.Symbol, 100)

        # set a stop market order to exit when SPY drops by 20%
        self.stopMarketOrder = self.StopMarketOrder(
            self.spy.Symbol,
            100,
            self.Securities[self.spy.Symbol].Price * 0.8,
        )

    def OnOrderEvent(self, orderEvent):
        if orderEvent.OrderId == self.stopMarketOrder.OrderId:
            self.Debug(f"Stop market order filled: {orderEvent}")
```

- sets a stop market order for a given symbol, number of shares, and market
  price
- the returned object has an `OrderId` attribute that can be compared against the
  object the event handler receives

## related

- [[qcalgorithmmarketorder]]

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/api-reference#StopMarketOrder-header
