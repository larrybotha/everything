---
tags:
  - resource/article
---

Link: https://algotrading101.com/learn/quantconnect-guide/


## Takeaways

- an Alpha is an algorithm that generates _Insights-_ predictions detailing whether an asset is expected to go up or down in price, and sometimes also the magnitude and duration to occur of the expected change
- Alpha Streams are algorithms in QC that can be leased to other users
- Lab/Terminal is where one creates algorithms
	- SDF, or Strategy Development Framework, is where one builds algorithms from existing components
	- the "Classic Method" is where code is written from scratch
- `QCAlgorithm` of the base class for creating algorithms
	- self.Initialize and self.onData are the foundation of a class
		- also see `OnHour()` or `OnEndOfDay()`
	- self.SetStartDate(2018, 4, 1) - date to start back test 
	- self.SetCash(100000) - starting cash
	- self.AddEquity() - tickers to eval
	- self.RSI - one of several methods for configuring technical indicators
	- self.SetWarmUp() - allow indicators to become populated before entering trades
	- self.Schedule.On(DateRule, TimeRule, Action) - schedule actions to be run at given times - see https://www.quantconnect.com/docs/algorithm-reference/scheduled-events
- QC has Jupyter Notebooks environments useful for visualisation 
- a limit order to buy SPY:
	```python
		# Purchase 10 SPY shares when its 5% below the current price
		close = self.Securities["SPY"].Close
		limitTicket = self.LimitOrder("SPY", 10, close * .95)
		```

- every Alpha module must return Insights.

	The Update method returns an array of Insight objects.

	An Insight is a single prediction for an asset

## Related

- [[What is Backtesting - 3 Aims of Backtesting]]
- [[Data Science Mental Models – Optimizing your Thinking and Decision-Making]]
- [[52 Trading Rules in 3 Minutes]]
## Links and resources

- https://www.quantconnect.com/terminal/#bootcamp
- https://www.quantconnect.com/docs/algorithm-reference/trading-and-orders
- https://www.quantconnect.com/docs/algorithm-reference/consolidating-data
- https://www.quantconnect.com/docs/algorithm-framework/alpha-creation
- datasets:
	- Quandl: https://algotrading101.com/learn/quandl-guide/
- Python tools:
	- https://www.quantstart.com/articles/backtesting-systematic-trading-strategies-in-python-considerations-and-open-source-frameworks/
	- https://algotrading101.com/learn/backtesting-py-guide/
	- https://algotrading101.com/learn/backtrader-for-backtesting/