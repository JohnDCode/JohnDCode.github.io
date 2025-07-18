---
title: Backtesting Engine Framework
description: An explanation and demonstration of a custom financial backtesting engine framework
author: John
date: 2025-07-18 01:00:00 +0800
categories: [Projects, Finance]
tags: [Projects, C++, Python]
media_subpath: '/assets/2025-07-18-Backtesting-Engine'
---


Recently I developed a C++ backtesting engine framework to simulate the performance of trading strategies with historical data. 



### What is a Backtesting Engine?

Backtesting is the process of evaluating a trading strategy by testing it against historical data. A backtesting engine is a software application that automates this process. A backtesting engine takes in historical market data and a set of algorithmic trading rules (the trading strategy). It then simulates the market by feeding the trading strategy data, and allowing the strategy to trade based on that data over time. Backtesting provides traders with insight into how a particular strategy might behave in the future based on its behavior in the past. 

<br />

### My Framework

I developed a high-performance backtesting engine, built as a modular C++ framework and distributed as a Python extension module (.so) via pybind11.

At its core, the engine simulates realistic market conditions, including:

- Dividend payments and stock splits
- Short selling and margin trading
- Slippage modeling (volume- and randomness-based)
- Order queue priority and latency simulation


This design allows users to write trading strategies in Python while leveraging the speed and rigor of a C++ simulation engine. Through the Python interface, users can define strategies, configure backtests, and run simulations seamlessly.

The engine is designed as a framework, such that users can build additional layers such as custom reporting, GUIs, or advanced analytics in python on top of the core C++ engine. This provides flexibility for both simple backtests and more sophisticated trading research pipelines.

<br />

### Use

<br />

### Demos

<br />

### Conclusion

<br />
