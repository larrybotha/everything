---
aliaes:
  - initialization
---

parent: [[+ quant connect]]

- the `QcAlgorithm.Initialize` method in an algorithm
- `self.SetCash(value: int)` allows for settings starting cash
- `self.SetStartDate(year: int, month: int, day: int)` allows for setting start date
- `self.SetEndDate(year: int, month: int, day: int)` allows for setting end date
- to subscribe to data for a specific symbol:

    ```python
    self.AddEquity(
      symbol: str,
      resolution: Resolution,
      fillDataForward: bool,
      leverage: int,
      extendedMarketHours: bool,
      dataNormalizationMode: DataNormalizationMode,
    )
    ```
- `self.MOMP(symbol: Symbol, period:int, resolution: Resolution)` allows for
  setting a _MomentumPercent` indicator

## links and resources

- [`AddEquity`](https://www.quantconnect.com/docs/v2/writing-algorithms/securities/asset-classes/us-equity/requesting-data#12-Properties)
- [`SetCash`](https://www.quantconnect.com/docs/v2/writing-algorithms/initialization#04-Set-Cash)
- [Asset Classes](https://www.quantconnect.com/docs/v2/writing-algorithms/securities/asset-classes)
