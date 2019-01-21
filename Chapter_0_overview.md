# Chapter 0: Overview

## Outline:
This chapter will briefly walk through different approaches to derive the Black-Scholes formula. Moreover, we will also introduce the structure of this book and how chapters are related. Hopefully this chapter will give the big picture and intrigue you to explore the milestone stone of the Mathematical Finance.

---

## What is the Black-Scholes Formula?
Blach-Scholes Formula is an analytical option pricing formula which gives a theoretical estimate of the price of European-options. 

The most important insight of the Black-Scholes Formula is that an European option can be priced regardless of its expected return from the investors which gives a single price that market participants are likely to agree. 

**Analytical pricing vs. Numerical pricing**

Option pricing includes 2 main approaches: analytical pricing and numerical pricing. Analytical pricing uses mathematics (often in great quantity) to derive an exact option pricing formula based on the model of asset prices, e.g. Black-Scholes Formula. On the other hand, numerical pricing uses computers and many repetitions of a simple procedure to arrive at an estimated option price, e.g. Monte Carlo Simulation. Note that Exact analytical solutions are rare, most of the analytical pricing formula have no closed-form solutions. Therefore, although numerical pricing may not be as elegant as analytical pricing, it is still widely used to price complex derivatives other than European options.

## The Big Picture: How to derive the Black-Scholes Formula?

There are many ways to derive or interpret Black-Scholes Formula. The most common ways are **_1) Black-Scholes Equation_**, **_2) Cox and Ross Discounted Expectation_**, **_3) Cox, Ross and Rubinstein Binomial Option Pricing_**. We now present summaries of these three methods. 

### 1. Black-Scholes Equation (1973)

$$
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2S^2\frac{\partial^2 V}{\partial t^2} + rS\frac{\partial V}{\partial S} - rV = 0
$$

### 2. Cox and Ross Discounted Expectation (1976)

$$
\tilde V(t) = \frac{V(t)}{B(t)} = V(t)e^{-rt}
$$
$$
\tilde V(t) = \mathop{\mathbb{E}}[\tilde V(T) | \tilde V(t)]
$$
$$
V(t)e^{-rt} = \mathop{\mathbb{E}}[V(T)e^{-rT}| V(t)]
$$
$$
V(t) = e^{-r(T-t)}\mathop{\mathbb{E}}[V(T)| V(t)]
$$
### 3. Cox, Ross and Rubinstein Binomial Option Pricing (1979)

![Binomial](img/Binomial_Options.png)

## The Structure of this book

To build up the intuition of the Black-Scholes Formula, instead of following the timeline, we will learn the above 3 derivations in the reverse chronological order. 

We first introduce the *Binomial Option Pricing Approach*. 
-   [Chapter 1: The Tree Approach I -- Binomial Branch](Chapter_1_binomial_branch.md) starts by modeling the asset as well as the derivative price using a 1-step binomial model, i.e. Binomial Branch. It gives us the simple intuition of replication arguments and the risk-neutral probabilities.
-   [Chapter 2: The Tree Approach II -- Binomial Tree](Chapter_2_binomial_tree.md) further extend the one-step binomial model to a *J-step Binomial Model*, i.e. *Binomial Tree*. This model will give us approximations to Black-Scholes pricing.

Next we explore the *Discounted Expectation Approach*
-   [Chapter 3: Review of Probability](Chapter_3_probability.md)
-   [Chapter 4: Martingale Approach](Chapter_5_martingale.md)
-   [Chapter 5: Pricing Foreign Exchange and Equities with Dividends](Chapter_6_dividends.md)
-   [Chapter 6: Derive the Black-Scholes Formula by the Martingale Approach](Chapter_7_BS_martingale.md)
  
Then we derive the Black-Scholes Formula by *solving the Black-Scholes Equation*.
-   [Chapter 7: Stochastic Differential Equations and Ito's lemma](Chapter_4_SDE_Ito.md)
-   [Chapter 8: Derive the Black-Scholes Partial Differential Equation](Chapter_8_BSPDE.md)
-   [Chapter 9: Derive the Black-Scholes Formula from the Black-Scholes Partial Differential Equation](Chapter_9_BS_BSPDE.md)

Last but not least, we discuss the basic implications of the Black-Scholes Formula by performing simple asympototic analysis. We will also briefly cover the topics such as *Implied Volatility* (Chapter 10) and *Greeks* (Chapter 11). This section is very important because it helps us understand the behaviour of the Black-Scholes Formula which is the basis of hedging and risk management.
-   [Chapter 10: Asymptotic Analysis of the Black-Scholes Formula and Implied Volatility](Chapter_10_asymptotic_IV.md)
-   [Chapter 11: Deriving Greeks](Chapter_11_greeks.md)


Without further ado, let's get started.



 





