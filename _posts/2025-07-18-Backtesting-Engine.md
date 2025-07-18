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

1. Download the Python extension module (.so) from the [project Github](https://github.com/JohnDCode/JDA-Backtesting-Engine-Publish).

1. In your Python development environment, install the following packages:

- yfinance
- numpy
- pandas

```bash
pip install yfinance, numpy, pandas
```

1. Download the main and user Python files from the [project Github](https://github.com/JohnDCode/JDA-Backtesting-Engine-Publish).

1. Create a "data" directory in the root of your Python development environment to store all market data.

```
/your_environment/
├── backtest_python.cpython-312-x86_64-linux-gnu.so
├── main.py
├── user.py
├── data/
```

1. Adjust the path to the Python extension module (.so) at the top of both Python files.

```python
sys.path.append(os.path.abspath("PATH_TO_SO_FILE"))
```

1. Follow the instructions in comments on user.py to configure the backtest.

1. Run main.py to perform the backtest.

This demo project simply pulls bar data from the Yahoo Finance API, imports it to the exposed components of the engine via pybind11, and then runs the backtest using the implemented user strategy from the "on_data" method in the MyStrategy class. However, this is simply one way to use the framework. The engine will run as long as the "on_data" method is implemented and all appropriate bar data is imported to the engine via properly formatted csv's:

```
Date,Close,High,Low,Open,Volume
```

This demonstrates the most basic behavior of the engine, simply performing a backtest based on imported data from Yahoo Finance. This behavior can be extended in Python to custom GUI's, reports, etc. as long as the "on_data" method is properly implemented and csv data is properly imported. 

<br />

### Demos

<br />

### Conclusion

<br />
