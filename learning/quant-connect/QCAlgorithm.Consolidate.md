parent: [[+ quant connect]]

```python
from datetime import timedelta


class Algo(QCAlgorithm):
    def Initialize(self):
        # ...
        self.spy = self.AddEquity("SPY", Resolution.Daily)

        # ...

        # consolidate prices using timedelta
        self.Consolidate(spy.Symbol, timedelta(minutes=15), self.handler)

        # or CalendarType
        self.Consolidate(spy.Symbol, CalendarType.Weekly, self.handler)

        # or Resolution
        self.Consolidate(spy.Symbol, Resolution.Hour, self.handler)

    def handler(self, bar):
        self.Debug(bar)
```

- accepts a ticker, a timeframe, and a callback, consolidating the ticker's
  price as a bar as an argument to the callback whenever a bar is generated
- a consolidator cannot consolidate data from the underlying data into a smaller
  timeframe

  e.g. consolidating daily data into minute bars doesn't make sense

- consolidators create different types of data depending on the underlying
  requested data:
  - [TradeBar](https://www.quantconnect.com/docs/v2/writing-algorithms/consolidating-data/consolidator-types/calendar-consolidators#02-Consolidate-Trade-Bars)
  - [QuoteBar](https://www.quantconnect.com/docs/v2/writing-algorithms/consolidating-data/consolidator-types/calendar-consolidators#03-Consolidate-Quote-Bars)
- all consolidated bars have common attributes:
  - `bar.Time` - the moment the bar was created
  - `bar.EndTime` - the time at the end of the bar
  - `bar.Price`

## links and resources

- https://www.quantconnect.com/docs/v2/writing-algorithms/consolidating-data/consolidator-types/calendar-consolidators
- https://www.lean.io/docs/v2/lean-engine/class-reference/classQuantConnect_1_1Data_1_1Consolidators_1_1CalendarType.html
