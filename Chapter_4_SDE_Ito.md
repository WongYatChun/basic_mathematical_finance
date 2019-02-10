# Chapter 4: Stochastic Differential Equations and Ito's Lemma

## Outline
This chapter will:



## 1. Brownian Motion

We model the evolution of the stock price as a stochastic process instead of a function. A **process** is a variable that changes with time *randomly*, whereas a **function** is a variable that changes with time with a *deterministic* behaviour. Therefore, we need to study the properties of stochastic processes. Firstly, we will focus on the **Brown Motion** which is the building block of stochastic processes.

A **Standard Brownian Motion** $$B(t)$$ is a continuous-time stochastic process under measure $$P$$ if and only if:
1. $$B(0) = 0$$
2. $$B(t) - B(s) \sim N(0, t-s), \qquad 0 \le s \le t \le T$$
3. $$B(k) - B(k-1)$$ and $$B(k+1) - B(k)$$ are independent $$\implies$$ non-overlapping Brownian motions are independent
4. The sample path of $$B(t)$$ are continuous
$$
B(t) = \sum^{n-1}_{i=0}{\sqrt{dt}\epsilon_i} \qquad \text{where } \epsilon_i \sim IID \; N(0,1)
$$

We can prove that:
-   $$\mathbb{E}[B(t)] = 0$$
-   $$Var(B(t)) = t$$
-   $$Std(t) = \sqrt{t}$$
-   $$Cov(B(s), B(t)) = Var(B(s)) = s$$

More on $$Cov(B(s), B(t)) = s$$:

$$
\begin{aligned}
Cov(B(s), B(t)) &= Cov(B(s), B(s) + B(t) - B(s)) \\
&= Cov(B(s), B(s)) + Cov(B(s), B(t) - B(s)) \\
&= Var(B(s)) + 0  \quad (\because \text{non-overlapping Brownian motions are independent}) \\
&= s
\end{aligned}
$$

The increment of a standard Brownian motion can be written in a differential form:

$$
dB(t) = B(t+dt) - B(t) = \sqrt{dt}\epsilon \quad \text{where } \epsilon \sim IID \; N(0,1)
$$

We can also prove that:
-   $$\mathbb{E}(dB(t)) = 0$$
-   $$Var(dB(t)) = dt$$
-   $$Std(dB(t)) = \sqrt{dt}$$
-   $$Cov(dB(s), dB(t)) = 0$$

Special properties of Brownian motions:
1.  Brownian motion is continuous everywhere and differentiable nowhere
    -   It cannot be differentiated using ordinary calculus
    -   We need Ito's calculus to find its derivatives
2.  Brownian motion has Markov Property
    -   The present value of the variable is the only relevant information for predicting the future. The past history of the variable and the way that the present has emerged from the past are irrelevant, i.e. Brownian motion has no memory.
3.  A Brownian Motion under $$P$$ measure is a martingale under $$P$$ measure, i.e. no drift under $$P$$ measure
    -   $$\mathbb{E}^{P}[B(t) | B(s)] = \mathbb{E}^{P}[B(s) + B(t) - B(s)| B(s)] = B(s) + \mathbb{E}^{P}[B(t) - B(s)| B(s)] = B(s)$$

We can generate a new stochastic process by incorporating a standard Brownian motion. For example, the process:
$$
A(t) = \sigma B(t) \sim N(0, \sigma^2 t)
$$
or in the differential form (Stochastic Differential Equation)
$$
dA(t) = \sigma dB(t) \sim N(0, \sigma^2 t)
$$

A is called Brownian Motion with variance $$\sigma^2$$.

Another example, the process:
$$
P(t) = \alpha t + \sigma B(t) \sim N(\alpha t, \sigma^2 t)
$$
or in the differential form (Stochastic Differential Equation)
$$
dP(t) = \alpha dt + \sigma dB(t) \sim N(\alpha t, \sigma^2 t)
$$

P is called Brownian Motion with drift $$\alpha$$ and variance $$\sigma^2$$, or arithmetic Brownian motion.

## 2. Ito's Lemma

**Ito's lemma** is a formula used to explicitly calculate the **stochastic differential equation (SDE)** that governs the dynamics of an arbitrary function given the stochastic process of the function's arguments. <u>**The key idea is that we need to do perform Taylor's expansion to the second order**</u>. 

### Multiplication rules for stochastic differentials
We take following multiplication rules for granted when $$dt \to 0$$

$$  
\begin{aligned}
&dB(x,t)dB(x,t) = dt \\
&dB(x,t)dt = 0 \\
&dt(dt)^k \to 0 \quad k \in \Re
\end{aligned}

$$

### Ito's Lemma with one space variable
Let $$x$$ follow the SDE $$dx = \mu_1 dt + \sigma_1 dB(x, t)$$, then the SDE of $$f(x, t)$$ given the stochastic process of $$x$$ is: 
$$
df(x,t) = \frac{\partial f}{\partial t} dt + \frac{\partial f}{\partial x} dx + \frac{1}{2}\frac{\partial^2 f}{\partial x^2} (dx)^2
$$

### Ito's Lemma with two space variables
Let $$x$$ follow the SDE $$dx = \mu_1 dt + \sigma_1 dB(x, t)$$, $$y$$ follow the SDE $$dy = \mu_2 dt + \sigma_2 dB(y, t)$$, with $$dB(x, t)dB(y, t) = \rho dt$$, then the SDE of $$f(x, y, t)$$ given the stochastic process of $$x$$ and $$y$$ is: 
$$
df(x,y,t) = \frac{\partial f}{\partial t} dt + \frac{\partial f}{\partial x} dx + \frac{\partial f}{\partial y} dy + \frac{1}{2}\Big[\frac{\partial^2 f}{\partial x^2} (dx)^2 + \frac{\partial^2 f}{\partial y^2} (dy)^2 + 2\frac{\partial^2 f}{\partial xy} (dxdy)\Big]
$$

## 3. Modeling of the stock price

To formulate the process of the derivative price, we need first model the stock price because it is observable in the market. One thing need special consideration is that due to the limited liability of financial assets, the stock price cannot be negative. Therefore, we cannot assume the stock price follows normal distribution. 

However, we can **model the return of the stock by assuming the returns are normally distribted** as they can be either negative or positive. Under this assumption, since $$ S(T) = S(t) e ^{a(T-t)}, \quad a \in \Re$$, the **stock price is then lognormally distributed** or follow a **Geometric Brownian Motion**. It turns out lognormal distribution works quite well in modelling the stock price, at least it assures that the stock price will never be negative.

The required rate of return of the stock $$S$$ can be represented as $$\frac{S(t+\Delta t)}{S(t)}$$. When $$\Delta t \to 0$$, it becomes $$\frac{dS(t)}{S(t)}$$. 

### 3.1. Model the stock price under P measure
Under $$P$$ measure, we can assume $$\frac{dS(t)}{S(t)}$$ has two parts:

$$
\frac{dS(t)}{S(t)} = \mu dt \; (\text{expected return})+ \sigma dB(t)\; (\text{unexpected return})
$$
-   The expceted return $$\mu dt$$ could be determined by CAPM which compensates the time value of money, inflation, and risks.
-   The unexpected return $$\sigma dB(t)$$ is a random variable that determines the deviation of the actual return from the expected return with a mean $$0$$ and a variance $$\sigma^2 dt$$.

Put them together, the stock return is normally distributed under measure $$P$$ with mean $$\mu dt$$ and variance $$\sigma^2 dt$$.

$$
\frac{dS(t)}{S(t)} = \mu dt + \sigma dB(t) \sim N(\mu dt , \sigma^2dt)
$$

or we can move the $$S(t)$$ to the right-hand side so that the SDE describes the process of the stock price in a differential equation.

$$
dS(t) = \mu S(t)dt + \sigma S(t)dB(t) \sim LN(\mu dt , \sigma^2dt)
$$

For simplicity, we can assume $$\mu$$ and $$\sigma$$ are constants. 

### 3.2. Model the stock price under Q measure

Similarly, we can also model the stock price in the risk-neutral world. Since all securities earn risk-free rate $$r$$, let $$B^{Q}(t)$$ be a standard Brownian motion under the risk-neutral measure $$Q$$, the stock return is normally distributed under measure $$Q$$ with mean $$r dt$$ and variance $$\sigma^2 dt$$.

$$
\frac{dS(t)}{S(t)} = r dt + \sigma dB^{Q}(t) \sim N(r dt , \sigma^2dt)
$$

or we can move the $$S(t)$$ to the right-hand side so that the SDE describes the process of the stock price in a differential equation.

$$
dS(t) = r S(t)dt + \sigma S(t)dB^{Q}(t) \sim LN(r dt , \sigma^2dt)
$$

### 3.3. Derive the Ito process of the log-price

Let $$p(S(t), t) = \ln S(t)$$, $$p(S(t),t)$$ is a *process* of $$t$$ and a *function* of $$S$$.
By simple partial differentiation, we get:
-   $$\frac{\partial p(S(t), t)}{\partial t} = 0$$
-   $$\frac{\partial p(S(t), t)}{\partial S(t)} = \frac{1}{S(t)}$$
-   $$\frac{\partial^2 p(S(t), t)}{\partial S(t)^2} = - \frac{1}{S(t)^2}$$

####Derive the Ito process of $$p(S(t),t)$$ using Ito's Lemma:

##### Under P measure:
$$
\begin{aligned}
dS(t) &= \mu S(t)dt + \sigma S(t)dB(t) \\ \\
dp(S(t), t) &= \frac{\partial p(S(t), t)}{\partial t} dt + \frac{\partial p(S(t), t)}{\partial S(t)} dS(t) + \frac{1}{2}\frac{\partial^2 p(S(t), t)}{\partial S(t)^2} (dS(t))^2 \\
&= 0 + \frac{1}{S(t)}(\mu S(t)dt + \sigma S(t) dB(t)) + \frac{1}{2}\Big(-\frac{1}{S(t)^2}\Big)(\mu S(t)dt + \sigma S(t) dB(t))^2 \\
&= (\mu - \frac{1}{2}\sigma^2)dt + \sigma dB(t)
\end{aligned}

$$

##### Under Q measure:
$$
\begin{aligned}
dS(t) &= r S(t)dt + \sigma S(t)dB^{Q}(t) \\ \\
dp(S(t), t) &= \frac{\partial p(S(t), t)}{\partial t} dt + \frac{\partial p(S(t), t)}{\partial S(t)} dS(t) + \frac{1}{2}\frac{\partial^2 p(S(t), t)}{\partial S(t)^2} (dS(t))^2 \\
&= 0 + \frac{1}{S(t)}(r S(t)dt + \sigma S(t) dB^{Q}(t)) + \frac{1}{2}\Big(-\frac{1}{S(t)^2}\Big)(r S(t)dt + \sigma S(t) dB^{Q}(t))^2 \\
&= (r - \frac{1}{2}\sigma^2)dt + \sigma dB^{Q}(t)
\end{aligned}

$$

### 3.3. Derive the Ito process of the stock price

Since $$p(t) = \ln S(t)$$, $$S(t) = e^{p(t)}$$
By simple partial differentiation, we get:
-   $$\frac{\partial S(t)}{\partial t} = 0$$
-   $$\frac{\partial S(t)}{\partial p(t)} = S(t)$$
-   $$\frac{\partial^2 S(t)}{\partial p(t)^2} = S(t)$$

####Derive the Ito process of $$p(S(t),t)$$ using Ito's Lemma:

##### Under P measure:
$$
\begin{aligned}
dp(S(t), t) &= (\mu - \frac{1}{2}\sigma^2)dt + \sigma dB(t) \\

dS(t) &= \frac{\partial S(t)}{\partial t}dt + \frac{\partial S(t)}{\partial p(t)}dp(t) + \frac{1}{2}\frac{\partial^2 S(t)}{\partial (p(t))^2}d(p(t))^2 \\

&= 0 + S(t)((\mu - \frac{1}{2}\sigma^2)dt + \sigma dB(t)) + \frac{1}{2}S(t)((\mu - \frac{1}{2}\sigma^2)dt + \sigma dB(t))^2 \\

&= \mu S(t) dt + \sigma S(t)dB(t))

\end{aligned}

$$

##### Under Q measure:
$$
\begin{aligned}
dp(S(t), t) &= (r - \frac{1}{2}\sigma^2)dt + \sigma dB^Q(t) \\

dS(t) &= \frac{\partial S(t)}{\partial t}dt + \frac{\partial S(t)}{\partial p(t)}dp(t) + \frac{1}{2}\frac{\partial^2 S(t)}{\partial (p(t))^2}d(p(t))^2 \\

&= 0 + S(t)((r - \frac{1}{2}\sigma^2)dt + \sigma dB^Q(t)) + \frac{1}{2}S(t)((r - \frac{1}{2}\sigma^2)dt + \sigma dB^Q(t))^2 \\

&= r S(t)dt + \sigma S(t)dB^Q(t))


\end{aligned}

$$

It shows that both $$S(t)$$ and $$p(t)$$ have the Markov property which is consistent with the weak form of the market efficiency. It means that the present stock price has reflected all the history information. One cannot make abnormal return by analysing the past history of the stock prices.

## 4. Popular Stochastic Processes

### 4.1. Arithmetic Brownian Motion:

$$
dp(t) = \alpha dt + \sigma dB(t)
$$

### 4.2. Geometric Brownian Motion
It is used to model the stock price.
$$
dS(t) = \mu S(t) dt + \sigma S(t) dB(t)
$$

### 4.3. Ornstein-Uhlenbeck (mean reversion) process

$$
dr(t) = a(\bar{r}-r)dt + \sigma dB(t)
$$

This process is used in **Vasicek model** to model short-term interest rate.
The parameter $$a>0$$ is called mean-reverting paramter. $$\bar{r}$$ is the long-term of the short rate. The short rate is pulled to $$\bar{r}$$ at rate $$a$$. Noted that in Vasicek Model, the short rate can become negative.

### 4.4. Square-root process

$$
dr(t) = a(\bar{r}-r)dt + \sigma \sqrt{r(t)} dB(t)
$$

This process is used in **Cox-Ingersoll-Ross model (CIR model)** to model short-term interest rate. It has the same mean-reverting dirft as that in the Vasicek model, but the diffution term ($$\sigma \sqrt{r(t)}$$) is proportional to $$\sqrt{r(t)}$$. This implies the volatility increases as the short rate increases.  In constrast to Vasicek model, the short rate in CIR model is always non-negative. 

In addition to short-term interest rate, square-root process can also model *dividend yields* and *stock return volatility*.

## 5. Ito's Calculus

As we have already discussed, Brownian motion is not differentiable, and hence, we cannot use ordinary calculus to perform differentiation or integration on stochastic equations. We need Ito's Calculus instead. 

---
**Case 1: $$ \int^t_0 d\ln S(s) $$**


For example, under $$P$$ measure, we want to derive the functional form of the stock price $$S(t)$$ from the differential form of the stock price:
$$
dS(t) = \mu S(t) dt + \sigma S(t) dB(t)
$$

or

$$
\frac{dS(t)}{S(t)} = \mu dt + \sigma dB(t)
$$

The ordinary calculus tells us that 
$$
\frac{d\ln S(t)}{dS(t)} = \frac{1}{S(t)} \to d\ln S(t)= \frac{dS(t)}{S(t)}
$$

It might be tempting to conclude:
$$
d\ln S(t) = \mu dt + \sigma dB(t)
$$

However, it is **wrong**. We can check it by differentiating $$d \ln S(t)$$ using Ito's Lemma:

$$
\begin{aligned}
d \ln S(t) &= \frac{\partial S(t)}{S(t)} dS(t) + \frac{1}{2} \frac{\partial^2 \ln S(t)}{S(t)^2} (dS(t))^2    \\
&= \frac{d S(t)}{S(t)} + \frac{1}{2} (- \frac{1}{S(t)^2})(dS(t))^2 \\
&= (\mu - \frac{1}{2}\sigma^2)dt + \sigma dB(t) \quad (\because dS(t) = \mu S(t) dt + \sigma S(t) dB(t))
\end{aligned}

$$

Therefore, for $$\sigma \ne 0$$, i.e. if there is a random term in the differential equation, ordinary calculus does not work. 

With the proper differential equation for $$d \ln S(t)$$ by Ito's Lemma, we can integrate this differential equation and find the function form of the stock price:

$$

\begin{aligned}
\int^t_{0} d \ln S(s) &= \int^t_{0} (\mu - \frac{1}{2}\sigma^2)ds + \sigma dB(s)    \\
\left. \ln S(s) \right |^t_0 &= \left.(\mu - \frac{1}{2}\sigma^2)s \right |^t_0 + \sigma B(s) \Big|^t_0 \\
\ln S(t) - \ln S(0)  &= (\mu - \frac{1}{2}\sigma^2)t +  \sigma (B(t) - B(0)) \\
\ln S(t)   &= \ln S(0) + (\mu - \frac{1}{2}\sigma^2)t +  \sigma B(t) \sim N(\ln S(0) + (\mu - \frac{1}{2}\sigma^2)t,\; \sigma t)\\
S(t) &= S(0) e^{(\mu - \frac{1}{2}\sigma^2)t +  \sigma B(t)} \sim LN(\ln S(0) + (\mu - \frac{1}{2}\sigma^2)t, \; \sigma t))
\end{aligned}

$$

Similarly, under $$Q$$ measure, given the differential form of the stock price 
$$
dS(t) = r S(t) dt + \sigma S(t) dB(t)
$$

We can derive the derive the differential form of the log-price process:

$$
\begin{aligned}
d \ln S(t) &= \frac{\partial S(t)}{S(t)} dS(t) + \frac{1}{2} \frac{\partial^2 \ln S(t)}{S(t)^2} (dS(t))^2    \\
&= \frac{d S(t)}{S(t)} + \frac{1}{2} (- \frac{1}{S(t)^2})(dS(t))^2 \\
&= (r - \frac{1}{2}\sigma^2)dt + \sigma dB(t) \quad (\because dS(t) = r S(t) dt + \sigma S(t) dB(t))
\end{aligned}

$$

Integrate $$d \ln S(t)$$:
$$
\begin{aligned}
\int^t_{0} d \ln S(s) &= \int^t_{0} (r - \frac{1}{2}\sigma^2)ds + \sigma dB(s)    \\
\left. \ln S(s) \right |^t_0 &= \left.(r - \frac{1}{2}\sigma^2)s \right |^t_0 +  \sigma B(s) \Big| ^t_0 \\
\ln S(t) - \ln S(0)  &= (r - \frac{1}{2}\sigma^2)t +  \sigma (B(t) - B(0)) \\
\ln S(t)   &= \ln S(0) + (r - \frac{1}{2}\sigma^2)t +  \sigma B(t) \sim N(\ln S(0) + (r - \frac{1}{2}\sigma^2)t,\; \sigma t)\\
S(t) &= S(0) e^{(r - \frac{1}{2}\sigma^2)t +  \sigma B(t)} \sim LN(\ln S(0) + (r - \frac{1}{2}\sigma^2)t, \; \sigma t))
\end{aligned}

$$

---

**Case 2: $$ \int^t_0 B(s) dB(s) $$**

It might be tempting to conclude:
$$
\int^t_0 B(s) dB(s) = \frac{1}{2} B(t)^2
$$

It is also **wrong**. Differentiating the RHS would not give the integral on LHS. In fact, we are not always be able to find the functional form of a SDE. It requires experience and possible luck to solve the SDE. With prior knowledge, we can solve $$ \int^t_0 B(s) dB(s) $$ by first differentiating $$dB(t)^2$$ by Ito's Lemma.

$$
\begin{aligned}
dB(t)^2 &= \frac{\partial B(t)^2}{B(t)} dB(t) + \frac{\partial^2 B(t)^2}{\partial B(t)^2}(dB(t)^2)^2 \\
&= 2B(t)dB(t) + dt
\end{aligned}
$$

We can try to integrate $$dB(t)^2$$ and see what it gives us:
$$
\begin{aligned}
\int^t_0 dB(s)^2 &= \int^t_0 2B(S)dB(s) + \int^t_0 ds \\

B(t)^2 & = 2 \int^t_0 B(S)dB(s) + t \\
\implies \int^t_0 B(s)dB(s) &= \frac{1}{2}(B(t)^2 - t)
\end{aligned}
$$

Therefore, we luckily find the solution for $$\int^t_0 B(s)dB(s) = \frac{1}{2}(B(t)^2 - t)$$










