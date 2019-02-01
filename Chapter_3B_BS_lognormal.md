# Chapter 3B: Black-Scholes Framework and Lognormal Distribution


## Outline
This chapter will:
1. Derive the probability of a European call is in the money in the risk-neutral world

## 1. Derive the probability of a European call is in the money in the risk-neutral world

### 1.1. Lognormal Distribution in Black-Scholes framework

In the Black-Scholes framework, in the risk-neutral world, the return of the stock price $$\ln(\frac{S(T)}{S(0)})$$ is assumed to be normally distributed, with the expected **arithmetic** return (not geometric) of the risk-free rate, i.e. $$\ln(\frac{S(T)}{S(0)}) \sim N((r-\frac{1}{2}\sigma^2)T, \sigma^2T$$. 

$$
\ln(\frac{S(T)}{S(0)}) \sim N((r-\frac{1}{2}\sigma^2)T, \sigma^2T) \\
$$
By simple transformation:
$$
\ln(S(T)) -\ln(S(0)) \sim N((r-\frac{1}{2}\sigma^2)T, \sigma^2T) \\
\ln(S(T)) \sim N(\ln(S(0)) + (r-\frac{1}{2}\sigma^2)T, \sigma^2T) \quad (\because \ln(S(0))  \text{is a constant})\\
$$

Therefore, the stock price (or the underlying price) at maturity $$S(T)$$ follows lognormal distribution.
$$
S(T) \sim LN(\ln(S(0)) + (r-\frac{1}{2}\sigma^2)T, \sigma^2T) 
$$

Under this setting, the expected return of the stock price at maturity $$T$$ in the risk-neutral world is exactly the risk-free rate:

$$

\mathbb{E}(S(T)) = e^{\ln(S(0))+(r-\frac{1}{2})T + \frac{1}{2}\sigma^2T} = S(0)e^{rT}
$$

---

### 1.2. The probability of the stock price is lower than the strike price in risk-neutral world

$$
\begin{aligned}
prob(S(T) \le K)    
&= prob(\ln(S(T)) \le ln(K)    \\
&= prob\Big( \frac{\ln(S(T)) - \big( \ln(S(0)) + (r - \frac{1}{2}\sigma^2)T \big)}{\sigma \sqrt{T}} \le \frac{\ln(K) - \big( \ln(S(0)) + (r - \frac{1}{2}\sigma^2)T \big)}{\sigma \sqrt{T}} \Big) \\
&= prob\Big( Z \le \frac{\ln(\frac{K}{S(0)}) - (r - \frac{1}{2}\sigma^2)T}{\sigma \sqrt{T}} \Big) \\
&= prob\Big( Z \le -\frac{\ln(\frac{S(0)}{K}) + (r - \frac{1}{2}\sigma^2)T}{\sigma \sqrt{T}} \Big) \\
&= \Phi\Big(-\frac{\ln(\frac{S(0)}{K}) + (r - \frac{1}{2}\sigma^2)T}{\sigma \sqrt{T}}\Big)\\

\text{Let} \: d_2 &= \frac{\ln(\frac{S(0)}{K}) + (r - \frac{1}{2}\sigma^2)T}{\sigma \sqrt{T}} \\

\end{aligned}
$$

$$
\text{Therefore: } \quad

prob(S(T) \le K) = \Phi(-d_2) = 1 - \Phi(d_2)


$$

### 1.3. The probability of the stock price is higher than the strike price in risk-neutral world
$$
prob(S(T) > K) = 1- prob(S(T) \le K) = 1- (1 - \Phi(d_2)) = \Phi(d_2)
$$

Therefore, the probability that a European call is in-the-money in the risk-neutral world is $$\Phi(d_2)$$