---
title: CLI Options Pricer
description: An explanation and demonstration of my Rust CLI tool used to price financial options
author: John
date: 2025-07-27 16:00:00 +0800
categories: [Projects, Finance]
tags: [Projects, Rust]
media_subpath: '/assets/2025-07-27-Options-Pricer'
---


This past month, I set out to learn (according to Stack Overflow's developer survey) the "most loved" programming language, Rust. This proved to be a rather daunting task, but after reading up on the language and then playing around with its various unique features, I decided to develop a project I had originally envisioned a few months prior. I created a cross-platform [CLI tool](https://github.com/JohnDCode/JDA-CLI-Options-Pricer-Publish) that allows users to instantly calculate fair prices for live financial options contracts. 



### Financial Options

An "option", according to [Wikipedia](https://en.wikipedia.org/wiki/Option_(finance)) is "a contract which conveys to its owner, the holder, the right, but not the obligation, to buy or sell a specific quantity of an underlying asset or instrument at a specified strike price on or before a specified date, depending on the style of the option". 

To those unfamiliar with the stock market, this may sound a bit daunting, so let me clarify with an example. As of writing this post, the symbol "AAPL" (Apple Inc) is trading for about US$214. I could purchase the stock for this price, or I could purchase an option that allows me to purchase this stock at a different price later. Just before the most recent market close, [a contract](https://finance.yahoo.com/quote/AAPL250801C00202500/) was purchased for AAPL. Let's examine this option. This option was a call option, meaning that by purchasing this contract, the owner now possesses the right to purchase the underlying asset (AAPL stock) at the strike price of the option. The strike price for this particular contract was US$202.50. This means that if the owner was to exercise this option, they could purchase the stock at the strike price of $202.50, regardless of what the current price of AAPL is. Now, let's suppose at the next market opening, the price of Apple Inc stock skyrockets to an incredible US$300. The owner of this contract would not have to pay the spot price of US$300 for the stock, but could exercise their option, and pay the strike price of US$202.50. 

There are various types of options and additional parameters that factor into the purchase of these contracts, but this suffices as the basic concept. 

<br />

### Pricing Models

Prior to the 1970's, there was no widely accepted mathematical method to price options contracts. Then, in 1973, Fischer Black, Myron Scholes, and Robert Merton developed the Black-Scholes model. This model can successfully estimate the theoretical worth of options contracts (and other derivates). This model was intended for use in European style options contracts.

However, for American contracts, there is an issue. Within each options contract contains an excersise or expiration date. For European style options, the option can only be excersised on such a date, while for American style options, the option can be excersised at anytime up until that date. Due to this difference, the Black-Scholes model fails to price American style options. As such, a different approach was required.

In 1979, John Cox, Stephen Ross, and Mark Rubinstein proposed the binomial options pricing model as an expasion to the Black-Scholes model. This model operated on the idea that at any given time step, an asset can either increase or decrease in value by particular weights. The original paper outlines how these "up" (u) and "down" (d) factors have particular probabilities of being applied to the stock at each timestep. By utilizing multiple time steps, where at each node the asset can either increase or decrease by the up and down factors, a binomial tree is formed with all possible options at the end of the steps:

![Binomial Tree](/binomialTree.png){: width="1086" height="395" }

<br />

### Rust CLI tool

Here


#### Examples

Here

<br />

### Documentation

Here


#### Auto

Here

#### Manual

Here
