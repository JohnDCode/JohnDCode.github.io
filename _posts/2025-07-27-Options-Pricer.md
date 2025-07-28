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

An "option", according to [Wikipedia](https://en.wikipedia.org/wiki/Option_(finance)), is "a contract which conveys to its owner, the holder, the right, but not the obligation, to buy or sell a specific quantity of an underlying asset or instrument at a specified strike price on or before a specified date, depending on the style of the option". 

To those unfamiliar with the stock market, this may sound a bit confusing, so let me clarify with an example. As of writing this post, the symbol "AAPL" (Apple Inc) is trading for about US$214. I could purchase the stock for this price, or I could purchase an option that allows me to purchase this stock at a different price later. Just before the most recent market close, [an option](https://finance.yahoo.com/quote/AAPL250801C00202500/) was purchased for AAPL. Let's examine this option. This option was a call option, meaning that by purchasing this contract, the owner now possesses the right to purchase the underlying asset (AAPL stock) at the strike price of the option. The strike price for this particular contract was US$202.50. This means that if the owner were to exercise this option, they could purchase the stock at the strike price of $202.50, regardless of what the current price of AAPL is. Now, let's suppose at the next market opening, the price of Apple Inc stock skyrockets to an incredible US$300. The owner of this contract would not have to pay the spot price of US$300 for the stock, but could exercise their option and pay the strike price of US$202.50. 

There are various types of options and additional parameters that factor into the purchase of these contracts, but this suffices as the basic concept. 

<br />

### Pricing Models

The purpose of this post is to demonstrate the CLI tool that utilizes these models, but I'll provide a brief overview of the development of these models and a high-level explanation of the ones I used. 

Prior to the 1970's, there was no widely accepted mathematical method to price options contracts. Then, in 1973, Fischer Black, Myron Scholes, and Robert Merton developed the Black-Scholes model. This model can successfully estimate the theoretical worth of European style options contracts (and other derivatives).

However, for American contracts, there is an issue. Within each option contract is an exercise or expiration date. For European style options, the option can only be exercised on such a date while for American style options, the option can be exercised at any time up until or on that date. Due to this difference, the Black-Scholes model fails to price American style options. As such, a different approach is required.

In 1979, John Cox, Stephen Ross, and Mark Rubinstein proposed the binomial options pricing model as an expansion to the Black-Scholes model. This model operated on the idea that at any given time, an asset can either increase (up) or decrease (down) in value by particular factors (u/d). Contrary to the Black-Scholes model, it assumes that prices move in discrete steps. At time t=1, an asset can exist as its price at t=0 multiplied by the up factor, or it can exist as its price at t=0 multiplied by the down factor. As the asset follows a multiplicative random walk, this creates a tree of future possible asset prices:

![Binomial Tree](/binomialTree.png){: width="1086" height="395" }
_Binomial Tree with 4 steps, diagram from [here](https://gregorygundersen.com/blog/2023/06/03/binomial-options-pricing-model/)_

In the above example, 4 steps are used to create a binomial tree. At the end of the tree, there are steps (n) + 1 nodes, leaving 5 distinct possibilities for the asset to reach after n steps. Each price is represented by S (the original price) multiplied by the respective degrees of applied up and down factors.

This basic concept of estimating the future movements of an asset using these trees is the basis of the binomial model for calculating American and European options values. 

Currently, due to difficulty finding reliable data sources for European options (such as the options chain), I have limited the functionality of this tool to pricing **American options with the CRR Binomial Pricing Model**. However, the binomial model has been proven to converge to the Black-Scholes model as the number of steps increases.

Once again, I've only provided a simple, overarching explanation on the binomial model. Here are two good sources to read more:

- [Macroption Article](https://www.macroption.com/cox-ross-rubinstein-formulas/)
- [NTU Paper](https://homepage.ntu.edu.tw/~jryanwang/courses/Financial%20Computation%20or%20Financial%20Engineering%20(graduate%20level)/FE_Ch04%20Binomial%20Tree%20Model.pdf)

<br />

### Rust CLI tool

This CLI tool has 2 modes / commands:

- Automatic
- Manual

See below for specific examples and all arguments/flags for each command, but here is a basic overview of each:

#### Automatic (auto)

Both of these commands are used to price American options using the binomial model. The unique aspect of automatic mode is that this command calculates the fair price of live options contracts pulled from the asset's live options chain. The user provides the asset symbol, a strike price, and the number of steps to run the binomial simulation. The tool then pulls all available option expiration dates from the symbol's option chain, and displays them to the user in a drop down menu. The user selects a date, and the CLI tool selects the options contract with the strike price closest to the provided strike price that also expires on that day. The tool then uses the data pulled from the options chain, relevant market data, and the risk free rate from U.S. treasury securities, to calculate the fair value of that options contract.

#### Manual

This command calculates the fair value of theoretical American options contracts. Rather than pulling live data, each aspect of the option is provided manually (spot price, strike price, etc.). The command then uses the binomial model to price the theoretical option.

<br />

### Arguments & Flags

#### Automatic (auto)

|Argument       |Short/Long                 |Description                                            |
|:---           |:----                      |:----                                                  |
|Symbol         |--symbol / -s \<SYMBOL\>   |The symbol to price                                    |
|Strike         |--strike / -k \<STRIKE\>   |The target strike price for the selected option        |
|Steps          |--steps / -n \<STEPS\>     |The number of steps in the binomial tree               |
|Call           |--call / -c                |Price a call option (default = true)                   |
|Put            |--put / -p                 |Price a put option (default = false)                   |

#### Manual

|Argument       |Short/Long                         |Description                                            |
|:---           |:----                              |:----                                                  |
|Spot           |--spot / -s \<SPOT\>               |The spot price of the asset                            |
|Strike         |--strike / -k \<STRIKE\>           |The strike price of the option                         |
|Time           |--time / -t \<STRIKE\>             |The time (in years) to expiration of the option        |
|Rate           |--rate / -t \<STRIKE\>             |The risk free interest rate                            | 
|Volatility     |--volatility / -v \<VOLATILITY\>   |The implied volatility of the option                   |
|Steps          |--steps / -n \<STEPS\>             |The number of steps in the binomial tree               |
|Call           |--call / -c                        |Price a call option (default = true)                   |
|Put            |--put / -p                         |Price a put option (default = false)                   |

<br />

### Examples

Note: I'm performing my tests on a Windows machine. The CLI is cross platform, with different versions being posted on the [project Github](https://github.com/JohnDCode/JDA-CLI-Options-Pricer-Publish).

#### Example 1: Automatically Pricing a Live Apple Call Option

Let's price a live Apple call option. We'll use the following command:

```powershell
options_pricer.exe auto -s AAPL -k 200 -n 10000
```

We do not need to specify the _--call_ flag, as the tool defaults to call options over put options.

The tool then asks us to select an expiration date. Using the arrow and enter keys, lets select _2025-08-29_:

![Auto Output 1](/autoOutput1.png){: width="1356" height="1009" }
_Powershell Window of Example 1_

After making our selection, we see the following output:

![Auto Output 2](/autoOutput2.png){: width="1356" height="1009" }
_Powershell Window of Example 1_

Our selected option has been priced at $US16.83!

#### Example 2: Manually Pricing a Theoretical Call Option

Now, let's price the same option we did as above, but using the manual command to change the expiration date to 1 year from now. The command then becomes:

```powershell
options_pricer.exe manual -s 213.95 -k 200 -t 1 -r 0.0424 -v 0.2965 -n 10000
```

This changes the output to:

![Manual Output 1](/manualOutput1.png){: width="1356" height="1009" }
_Powershell Window of Example 2_

As we can see, the difference in expiration date has increased the price of the option to $36.64.

<br />

### Conclusion

Altogether, I am satisfied with this project. However, I did not fulfill my original goal of including support for the Black-Scholes model. As such, in the future I plan to add the following features:

- Black-Scholes Model
- Automatic and Manual European Options
- Calculation of "The Greeks"

Despite failure on the European support front, I still learned quite a bit. 

Once again, the compiled binaries can be found on the [project Github](https://github.com/JohnDCode/JDA-CLI-Options-Pricer-Publish).
