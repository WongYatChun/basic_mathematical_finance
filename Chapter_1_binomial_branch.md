# Chapter 1: Binomial Branch

## Outline
This chapter will:
1. Introduce the Binomial Branch
2. Introduce the Risk-Neutral Probability
3. Introduce the basic of Martingale
4. Introduce a 5-step risk-neutral derivative rule in the binomial branch framework


## 1. Introduce the Binomial Branch

$$B(t)$$: the price of a riskless money market instrument, e.g. a Cash Bond
-  $$B(t) = e^{rt}$$
   -  $$r$$: continuously compounded risk-free rate


## 2. Introduce the Risk-Neutral Probability

### 2.1. Glossary

*(Note: The definitions below are not rigorous, but it serves for this book to give an intuition)*

**Arbitrage**: The simultaneous buying and selling of a security at two different prices in two different markets, resulting in profits wihtout risk. 
-  Perfectly efficient markets present no arbitrage opportunities.
-  In reality, arbitrage opportunities seldom exist and are often precluded because of transaction costs

**The Law of One Price**: If two securities have the same payoffs in the future, then they must have the same price today.
-  Otherwise, there is an arbitrage opportunity


### 2.2. Replicating Portfolio and Risk-neutral Probability

We will find the **risk-neutral probability** by applying the law of one price

We use the stock and the cash bond to build a porfolio which mimics the payoffs of the derivative. This portfolio is called "**replicating portfolio**". Since the replicating portfolio and the derivative have the same payoff structure, by *The Law of One Price*, **<u>their prices must be the same</u>**.

Suppose:

-  $$f_0$$: price of the derivative

-  $$\Delta$$: number of shares of the stocks/underlying

-  $$B$$: number of shares of the riskless bond

Since the price of the derivative equals the price of the replicating portfolio, we have:

$$\text{At time = }0$$:
$$
f_0 = \Delta s_0 + B
$$
$$\text{And at time = }\Delta t$$:
$$
\begin{cases}
   f_u = \Delta s_u + B e^{r\Delta t} \\
   f_d = \Delta s_d + B e^{r\Delta t}
\end{cases}
$$
Solve system of equations, we get:

$$
\begin{cases}
   \Delta = \frac{f_u - f_d}{s_u - s_d} \\
   B =  \frac{e^{-r\Delta t}(f_d s_u - f_u s_d)}{s_u = s_d}
\end{cases}
$$

Substitute $$\Delta$$ and $$B$$ into $$f_0 = \Delta s_0 + B$$
$$
f_0 = \Delta s_0 + B = e^{-r\Delta t}\left(\frac{e^{r\Delta t}s_0 - s_d}{s_u - s_d}f_u + \left(1 - \frac{e^{r\Delta t}s_0 - s_d}{s_u - s_d}\right)f_d\right)

$$
## 3. The basic of Martingale

### 3.1. Glossary

*(Note: The definitions below are not rigorous, but it serves for this book to give an intuition)*

**Measure**: The formal definition is too obscure for the purpose of this book. In probability theory, a "measure" is a mathematical function that allocates probability weight to outcomes in the sample space. Two probability measures that reassign probabilities to outcomes without changing the range of possible outcomes as called **"equivalent measures"**.

**Martingale**: A process $$X_t$$ with respect to a measuure $$P$$ if it satisfies the following two conditions:
   -  $$\mathop{\mathbb{E}}^P[X_T | X_t, ..., X_0] = \mathop{\mathbb{E}}^P[X_T | X_t ] = X_t$$
   -   $$\mathop{\mathbb{E}}^P[| X_T |] < \infty$$ for all $$T$$

**Martingale Measure**: The measure that makes a process a martingale

**Real-world measure $$P$$**: The measure that models the probability distribution of the market prices at a given future investment horizon.


**Risk-neutral measure $$Q$$**: The risk-neutral measure makes the risk-free discounted stock price (as well as the risk-free discounted derivative) a martingale, also called "**equivalent martingale measure"**.
   -   Uniqueness of the measure $$Q$$: In a discrete-time world, for any stock process, there will be a unique measure $$Q$$ under which the discounted stock is a $$Q$$-martingale

### 3.2. How to find the measure $$Q$$?
Premise: Measure $$Q$$ is the measure that makes the risk-free discounted stock price a martingale

**<u>In the binomial tree model</u>**:

Given a tree structure, if we can find a measure $$Q$$ that makes the risk-free discounted stock price process a martingale, then the risk-free discounted derivative will also be a $$Q$$-martingale. The price of the derivative today is therefore the expected discounted future payoffs at the risk-free rate under $$Q$$-measure


## 4. Five-step risk-neutral derivative rule in the binomial branch framework

**Step 1**: Discount the stock price $$S_{\Delta t}$$ by using the risk-free rate to have discounted stock price
-   $$e^{r\Delta t}S_{\Delta t}$$

**Step 2**: Find a measure $$Q$$ that makes the discounted stock price a martingale:

-   $$  \mathop{\mathbb{E}}^Q[e^{r\Delta t}S_{\Delta t}| e^{r * 0 }S_0] = e^{r * 0 }S_0 = S_0 $$

-   <u>Specifically, in the binomial tree model</u>:

    -   $$ s_0 = qe^{-r\Delta t}s_u + (1 - q)e^{-r\Delta t}s_d \implies q = \frac{e^{-r\Delta t}s_0 - s_d}{s_u - s_d}$$

**Step 3**: Discount the derivative price $$F_{\Delta t}$$ by using the risk-free rate to have discounted derivative price
-   $$e^{r\Delta t}F_{\Delta t}$$

**Step 4**: Calculate the expectation of the discounted derivative price under measure $$Q$$:
-   $$  \mathop{\mathbb{E}}^Q[e^{r\Delta t}F_{\Delta t}| e^{r * 0 }F_0] = e^{r * 0 }F_0 = F_0 $$

-   <u>Specifically, in the binomial tree model</u>:
    -   Plug in the $$q$$ calculated in Step 2
    -   $$ f_0 = qe^{-r\Delta t}f_u + (1 - q)e^{-r\Delta t}f_d$$

**Step 5**: Calculate the hedge ratio
-   To mimic payoffs of the derivative, we construct a replicating portfolio by:
    1.  Long $$x = \frac{f_u - f_d}{s_u - s_d}$$ stock, and
    2.  Make up the balance of the price of the derivative by riskless borrowing or lending