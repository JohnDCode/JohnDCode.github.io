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

Prior to the 1970's, there was no widely accepted mathematical method to price options contracts. Then, in 1973, Fischer Black, Myron Scholes, and Robert Merton developed the Black-Scholes model. This model can successfully estimate the theoretical worth of European style options contracts (and other derivatives).

However, for American contracts, there is an issue. Within each option contract is an exercise or expiration date. For European style options, the option can only be exercised on such a date, while for American style options, the option can be exercised at any time up until or on that date. Due to this difference, the Black-Scholes model fails to price American style options. As such, a different approach is required.

In 1979, John Cox, Stephen Ross, and Mark Rubinstein proposed the Binomial options pricing model as an expansion to the Black-Scholes model. This model operated on the idea that at any given time, an asset can either increase (up) or decrease (down) in value by particular factors (u/d). At time t=1, an asset can exist as its price at t=0 multiplied by the up factor, or it can exist as its price at t=0 multiplied by the down factor. As the asset follows a multiplicative random walk, this creates a tree of future possible asset prices:

![Binomial Tree](/binomialTree.png){: width="1086" height="395" }
_Binomial Tree with 4 steps_

In the above example, 4 steps are used to create a binomial tree. At the end of the tree, there are steps (n) + 1 nodes, leaving 5 distinct possibilities for the asset to reach after n steps. Each price is represented by S (the original price) multiplied by the respective degrees of applied up and down factors.

This tree forms the basis for the Binomial model, which is utilized in this project to estimate the fair price of American options. Currently, due to difficulty finding reliable data sources for European options (such as the options chain), I have limited the functionality of this tool to pricing American options with the Binomial model. However, the Binomial model has been proven to converge to the Black-Scholes model as the number of steps increases.



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
