---
title: Backtesting Engine Framework
description: An explanation and demonstration of my custom financial backtesting engine framework
author: John
date: 2025-07-18 01:00:00 +0800
categories: [Projects, Finance]
tags: [Projects, C++, Python]
media_subpath: '/assets/2025-07-18-Backtesting-Engine'
---


Recently I developed a C++ backtesting engine framework to simulate the performance of trading strategies with historical data. 



### What is a Backtesting Engine?

Backtesting is the process of evaluating a trading strategy by testing it against historical data. A backtesting engine is a software application that automates this process. A backtesting engine takes in historical market data and a set of algorithmic trading rules (the trading strategy). It then simulates the market by feeding the trading strategy data and allowing the strategy to trade based on that data over time. Backtesting provides traders with insight into how a particular strategy might behave in the future based on its behavior in the past. 

<br />

### My Framework

I developed a high-performance backtesting engine, built as a modular C++ framework and distributed as a Python extension module (.so) via pybind11.

At its core, the engine simulates realistic market conditions, including:

- Dividend payments and stock splits
- Short selling and margin trading
- Slippage modeling (volume- and randomness-based)
- Order queue priority and latency simulation


This design allows users to write trading strategies in Python while leveraging the speed and rigor of a C++ simulation engine. Through the Python interface, users can define strategies, configure backtests, and run simulations seamlessly.

The engine is designed as a framework, such that users can build additional layers such as custom reporting, GUIs, or advanced analytics in Python on top of the core C++ engine. This provides flexibility for both simple backtests and more sophisticated trading research pipelines.

<br />

### Using the Framework

Here is how to setup a basic environment for utilizing the framework:

`1.` Download the Python extension module (.so) from the [project Github](https://github.com/JohnDCode/JDA-Backtesting-Engine-Publish).

`2.` In your Python development environment, install the following packages:

- yfinance
- pandas

```bash
pip install yfinance, pandas
```

`3.` Download the main and user Python files from the [project Github](https://github.com/JohnDCode/JDA-Backtesting-Engine-Publish).

`4.` Create a "data" directory in the root of your Python development environment to store all market data.

```
/your_environment/
├── backtest_python.cpython-312-x86_64-linux-gnu.so
├── main.py
├── user.py
├── data/
```

`5.` Adjust the path to the Python extension module (.so) at the top of both Python files.

```python
sys.path.append(os.path.abspath("PATH_TO_SO_FILE"))
```

`6.` Follow the commented instructions in user.py to configure the backtest.

`7.` Run main.py to perform the backtest.

This demo project simply pulls bar data from the Yahoo Finance API, imports it to the exposed components of the engine via pybind11, and then runs the backtest using the implemented user strategy from the "on_data" method in the MyStrategy class. However, this is simply one way to use the framework. The engine will run as long as the "on_data" method is implemented and all appropriate bar data is imported to the engine via properly formatted csv's:

```
Date,Close,High,Low,Open,Volume
```

This demonstrates the most basic behavior of the engine, simply performing a backtest based on imported data from Yahoo Finance. This behavior can be extended in Python to custom GUI's, reports, etc. as long as the "on_data" method is properly implemented and csv data is properly imported. 

<br />

### Demos

To demonstrate the core C++ engine, I have designed 2 trading strategies that I will backtest using the engine. I have implemented the engine in the same manner as the above technique. Both backtests will be performed over the course of only 1 year (2024-07-15 - 2025-07-15) with a bar data size of 60 minutes. Additionally, each portolio will begin with $5,000 (USD).


- Note, I make use of the ```collections``` and ```numpy``` packages in these examples, which was not listed on the original list of package dependencies.


#### Strategy 1: Pairs Trading

Oftentimes there exists pairs of assets that are historically coorelated. Pairs trading involves measuring when two correlated assets move away from one another, and betting that the assets will eventually collapse back towards one another. To measure ths difference in correlated assets, Bollinger Bands are used to detect if one of the assets is overbought or oversold relative to recent history. If one asset drifts away from a mean value, the trader bets on the two assets converging together once again. Here, I have implemented this strategy using ```SPY``` and ```QQQ```.

```python
class MyStrategy(backtest_python.Strategy):

    # Bands will use last 200 bars as reference for each symbol
    window = 200
    spyHistory = collections.deque(maxlen=window)
    qqqHistory = collections.deque(maxlen=window)

    def __int__(self, order_m):
        super().init_(order_m)

    def on_data(self, bars, portfolio):

        # Get the close price of both symbols
        spyClose = bars["SPY"].close
        qqqClose = bars["QQQ"].close

        # Record the close prices for this bar
        self.spyHistory.append(spyClose)
        self.qqqHistory.append(qqqClose)

        # The strategy must have witnessed 1 full window to have proper reference
        if len(self.spyHistory) < self.window:
            return

        # Calculate hedge ratio (β) using linear regression
        beta = numpy.polyfit(self.qqqHistory, self.spyHistory, 1)[0]

        # Calculate spread
        spread = spyClose - beta * qqqClose

        # Calculate mean and standard deviation
        mean = numpy.mean([
            spy - beta * qqq for spy, qqq in zip(self.spyHistory, self.qqqHistory)
        ])
        std = numpy.std([
            spy - beta * qqq for spy, qqq in zip(self.spyHistory, self.qqqHistory)
        ])

        # Calculate zscore
        zscore = (spread - mean) / std


        # Retrieve the positions of both assets
        spyPosition = portfolio.get_position("SPY")
        qqqPosition = portfolio.get_position("QQQ")


        # Market Order Checks


        # Entry signals

        # SPY is at unusually high price, QQQ is at unusually low price
        if zscore > 2:
            self.sell("SPY", 10)
            self.buy("QQQ", 10)

        # SPY is at unusually low price, QQQ is at unusually high price
        elif zscore < -2:
            self.buy("SPY", 10)
            self.sell("QQQ", 10)

        # Exit signals (mean reversion)

        # Assets have converged back together
        elif abs(zscore) < 0.1:
            if spyPosition != 0:
                self.sell("SPY", spyPosition)
            if qqqPosition != 0:
                self.buy("QQQ", -qqqPosition)

```

```
=================== Strategy Performance Summary ===================

Starting Cash:        $5,000
Final Cash:           $114,114
Final Equity:         $7,911.11

====================================================================
```

Despite the backtest only being over the course of 1 year, this strategy was profitable.

- Note: The engine does not automatically close all positions upon termination of the backtest. As such, this strategy had a short position in SPY at the end of the test, leading to the abnormally high cash level in the portfolio. 

#### Strategy 2: Momentum Trading

Strategy Description

```python
The Strategy
```

```
The Results
```

<br />

### Conclusion

Here
