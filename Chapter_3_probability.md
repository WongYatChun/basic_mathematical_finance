# Chapter 3: Review of Probability and Statistics

## Outline
This chapter will:
1. Review the concept of Expectation, Variance, Covariance, and Correlation
2. Introduce normal distribution and central limit theorem
3. Introduce log-normal distribution
4. Derive the probability of a European call is in the money in the risk-neutral world


## 1. Expectation, Variance, Covariance, and Correlation

### 1.1. Expectation

If $$X$$ is a random variable whose value is in the range of $$[a, b]$$ and its probability density function (PDF) is $$f(x)$$, then the *expected value* of $$X$$, denoted by $$\mathbb{E}(X)$$, is defined by:

$$
\mathbb{E}(X) = \int^b_a f(x) dx
$$

The expectation of any function of X (denoted by $$p(x)$$) is defined by:

$$
\mathbb{E}(X) = \int^b_a p(x)f(x) dx
$$

#### Properties of Expectation
For random variables $$X$$ and $$Y$$, and constants $$a$$ and $$b$$

1.  $$\mathbb{E}(a) = a$$
2.  $$\mathbb{E}(aX) = a\mathbb{E}(X)$$
3.  $$\mathbb{E}(aX + b) = \mathbb{E}(X) + b$$
4.  $$\mathbb{E}(X + Y) = \mathbb{E}(X) + \mathbb{E}(Y) $$
5.  If $$X$$ and $$Y$$ are independent, then $$\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y) $$
6.  If $$\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y) $$, then $$X$$ and $$Y$$ are uncorrelated (but not necessarily independent)
7.  If $$X$$ and $$Y$$ are not independent, then $$\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y) + Cov(X,Y)$$
    -   $$Cov(X,Y)$$ denotes the covariace between X and Y

#### Conditional Expectation of a time-variant random variable

**Conditional expectation** of a time-variant random variable $$X(t)$$, given the information $$X(s)$$, $$ s < t$$, is usually denoted by:

$$
\mathbb{E}(X(t) | X(s))
$$

It means we take the expectation of a random variable $$X$$ at a future time $$t$$, given the information of $$X$$ at time $$s$$.

On the other hand, the conditional expectation of $$X(s)$$ given the information of $$X(s)$$ is:

$$
\mathbb{E}(X(s) | X(s)) = X(s)
$$

### 1.2. Variance

The variance of $$X$$, denoted by $$Var(X)$$ is defined by:

$$
Var(X) = \mathbb{E}((X - \mathbb{E}(X))^2) = \mathbb{E}(X^2) - (\mathbb{E}(X))^2
$$

#### Properties of Variance
For random variables $$X$$ and $$Y$$, and constants $$a$$ and $$b$$
1.  $$Var(a) = 0$$
2.  $$Var(aX) = a^2 Var(X)$$
3.  $$Var(aX + b) = a^2 Var(X)$$
4.  $$Var(X + Y) = Var(X) + Var(Y) + 2Cov(X,Y)$$
    -   $$Cov(X,Y)$$ denotes the covariace between X and Y

**Standard Deviation** of a random variable $$X$$, denoted by $$STD(X)$$, is defined by

$$
STD(X) = \sqrt{Var(X)}
$$

### 1.3. Covariance and Correlation

The covariance of any two random variables $$X$$ and $$Y$$, denoted by $$Cov(X,Y)$$, is defined by:

$$
Cov(X,Y) = \mathbb{E}((X - \mathbb{E}(X)))(Y - \mathbb{E}(Y)) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y)
$$

#### Properties of Covariance
For random variables $$X$$, $$Y$$ $$X_1$$ and $$X_2$$, and constants $$a$$ and $$b$$
1. $$Cov(a,b) = 0$$
2. $$Cov(a, X) = 0$$
3. $$Cov(aX, Y) = aCov(X,Y)$$
4. $$Cov(aX, bY) = abCov(X,Y)$$
5. $$Cov(aX + b, Y) = aCov(X,Y)$$
6. $$Cov(X,Y) = Cov(Y,X)$$
7. $$Cov(X, X) = Var(X)$$
8. $$Cov(X_1 + X_2, Y) = Cov(X_1, Y) + Cov(X_2, Y)$$
9. If $$X$$ and $$Y$$ are independent, then $$Cov(X,Y) = 0$$
   -   But the reverse is not always true
   -   For two joinly normally distributed variables $$X$$ and $$Y$$, if $$Cov(X,Y) = 0$$, $$X$$ and $$Y$$ are independent
10. If $$Cov(X,Y) = 0$$ and $$Cov(f(X),g(Y)) = 0$$ then $$X$$ and $$Y$$ are independent
    -   $$f(X)$$ and $$g(X)$$ are any nonlinear function of $$X$$ and $$Y$$ respectively

#### Correlation

The correlation between random variables $$X$$ and $$Y$$, denoted by \rho(X,Y), is defined by:

$$
\rho = \frac{Cov(X,Y)}{\sqrt{Var(X)}\sqrt{Var(Y)}}
$$

It can be shown that $$ -1 \le \rho(X,Y) \le 1$$.

If $$X$$ and $$Y$$ are linearly related by the equation $$Y = a + bX$$, then

$$

\rho(X, Y) = 
\begin{cases}
1 &  b > 0 \\
-1 & b < 0
\end{cases}

$$

### 1.4. Sample Mean and Sample Variance
Let $$x_1, x_2, \dots , x_n$$ be a sample of a random variable $$X$$ with a population mean $$\mu$$ and a population variance $$\sigma^2$$

**Sample Mean** $$\bar{x}$$: an estimation of the population mean $$\mu$$

$$
\bar{x} = \frac{1}{n} \sum^{n}_{i=1}x_i
$$

**Sample Variance** $$s^2$$: an estimation of the population variance $$\sigma^2$$

$$
s^2 = \frac{1}{n-1} \sum^{n}_{i=1}{(x_i-\bar{x})^2}
$$


## 2. Normal Distribution and Central Limit Theorem

### 2.1 Discrete Process vs. Continuous Process

**Discrete Process**: A process whose value changes on distinct, separated time points. For example, the binomial tree model describes the price of securities as a discrete process. The price changes at discrete time points with a fixed step size $$\Delta t$$.

**Continuous Process**: A process whose value changes at a real-valued time, allowing infinite divisibility of time. It can be precerived as taking a limit of a discrete process when $$\Delta t\to 0$$. It is preferable for two reasons:
1.  It is more realistic because it allows infinite possible state at each $$\delta t$$
2.  It is easier to derive formula

### 2.2 Probability Density Function

**Probability density function (PDF)** of a random variable $$X$$, denoted by $$f(x)$$, determines the probabilities associated with $$X$$. The probability that $$X$$ assumes a value between $$a$$ and $$b$$ where $$a < b$$, denoted by $$prob(a \le X \le b)$$, is equal to the area under $$f$$ between $$a$$ and $$b$$.

### 2.3. Normal Distribution and Central limit Theorem

**Normal distribution** is determined soleby two parameters: the mean $$\mu$$ and the variance $$\sigma^2$$, its PDF is given by:

$$
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^\frac{-(x - \mu)^2}{2\sigma^2} \\
\text{where } \quad -\infty < x < +\infty, \qquad -\infty < \mu < +\infty, \qquad \sigma > 0
$$

If $$X$$ is is a normal random variable with mean $$\mu$$ and variance $$\sigma^2$$, then we denote it as $$X \sim N(\mu, \sigma^2)$$

The **Cumulative Distribution Function (CDF)** of a normal random variable $$X$$, denoted by $$F(x)$$, determines the probability of the value of $$X$$ not greater than $$x$$:

$$
F(x) = prob(X \le x) = \int^{x}_{-\infty}f(y)dy
$$

The derivative of a random variable's CDF is its PDF, i.e. $$F'(x) = f(x)$$

#### Properties of the Normal Cumulative Distribution Function
1.  $$F(+\infty) = 1$$
2.  $$F(-\infty) = 0$$
3.  $$F(\mu) = \frac{1}{2}$$
4.  If $$ x_1 \le x_2$$, then $$F(x_1) \le F(x_2)$$
5.  $$prob(a < x \le b) = F(b) - F(a)$$
6.  $$prob(x = a) = F(a) - F(a-0) = 0$$