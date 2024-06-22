# W3 Quiz2 MLE Properties

## 知识要点

> 效率计算方法：
> $$Efficiency = \frac{CRLB(\theta)}{Var(\hat{\theta})}$$

## Question 1

Let $X_1, X_2, \ldots, X_n$ be a random sample from the exponential distribution with rate $\lambda > 0$.
Let $\hat\lambda$ be the maximum likelihood estimator of $\lambda$.
Compute the efficiency of $\hat\lambda$.

### 1 CRLB of $\lambda$

$$
CRLB(\lambda) = \frac{1}{I_n(\lambda)} = \frac{1}{n/\lambda^2} = \frac{\lambda^2}{n}
$$

### 2 Efficiency of $\hat\lambda$

#### Variance of $\hat\lambda$

$$
Var(\hat\lambda) = Var(\frac{1}{\bar{X}}) \\ = E[\frac{1}{\bar{X}^2}] - E^2[\frac{1}{\bar{X}}] \\ = E[\frac{1}{\bar{X}^2}] - \frac{n\lambda}{n-1}
$$

suppose $Y ~ \Gamma(\alpha, \beta)$, then $E[\frac{1}{\bar{X}^2}] = E[\frac{n^2}{Y^2}]$

对$E[\frac{n^2}{Y^2}]$计算后得到

$$
E[\frac{n^2}{Y^2}] = n^2 \lambda^2 \frac{\Gamma(n - 2)}{\Gamma(n)} \int ... (=1) \\ = \frac{n^2\lambda^2}{(n-1)(n-2)}
$$

所以 Variance of $\hat\lambda$ 为

$$
Var(\hat\lambda) = \frac{n^2\lambda^2}{(n-1)(n-2)} - \frac{n\lambda}{n-1} \\ = \frac{n^2\lambda^2}{(n-1)^2(n-2)} 
$$

#### Efficiency

$$
Efficiency = \frac{CRLB(\lambda)}{Var(\hat\lambda)} = \frac{\lambda^2}{n} \cdot \frac{(n-1)^2(n-2)}{n^2\lambda^2} \\ = \frac{(n-1)^2(n-2)}{n^3} \longrightarrow 1, \space as \space n \rightarrow \infty
$$

## Question 2

Let $X_1, X_2, \ldots, X_n$ be a random sample from the exponential distribution with rate $\lambda > 0$.
Find the asymptotic distribution of the maximum likelihood estimator for the "tail probability" $P(X > 1)$ for some fixed $x > 0$.

(Note: You do not actually need to find the MLE itself!)

A. $N(\lambda, e^-2\lambda/n)$
B. $N(e^{-\lambda}, 1/(n\lambda^2))$
C. $N(e^{-\lambda}, \lambda^2e^{-2\lambda}/n)$
D. $N(\lambda, \lambda^2/n)$


这是一个关于极大似然估计（MLE）的问题，特别是关于指数分布的尾部概率的MLE。我们知道，对于指数分布，其概率密度函数为 $f(x|\lambda) = \lambda e^{-\lambda x}$，其中 $\lambda > 0$ 是分布的参数，$x > 0$。

首先，我们需要找到尾部概率 $P(X > 1)$ 的MLE。这个概率可以通过累积分布函数（CDF）来计算，对于指数分布，其CDF为 $$F(x;\lambda) = 1 - e^{-\lambda x}$$。因此，尾部概率为 $$P(X > 1) = 1 - F(1;\lambda) = e^{-\lambda}$$。

然后，我们需要找到这个尾部概率的MLE的渐近分布。这通常涉及到大数定律和中心极限定理。在这个问题中，我们不需要找到MLE本身，而是需要找到它的渐近分布。

根据以上信息，我们可以看到选项中的每一个都是正态分布 $N(\mu, \sigma^2)$ 的形式，其中 $\mu$ 是均值，$\sigma^2$ 是方差。我们需要找到一个选项，其均值和方差与尾部概率 $e^{-\lambda}$ 的MLE的渐近分布相匹配。

在大样本极限下，最大似然估计量（MLE）的分布通常可以用正态分布来近似。对于这个问题，我们关心的参数是 $e^{-\lambda}$，这是一个关于原始参数 $\lambda$ 的函数。在这种情况下，我们可以使用**delta方法**来找到新参数的MLE的渐近分布。

简单来说，delta方法是一种用于找到一个函数的参数的方差的方法。如果我们有一个随机变量 $X$，其均值为 $\mu$ 和方差为 $\sigma^2$，并且我们关心的是 $g(X)$ 的分布，其中 $g()$ 是一个函数，那么 $g(X)$ 的方差可以用以下公式来近似：

$Var(g(X)) \approx [g'(\mu)]^2 \sigma^2$

在这个问题中，我们关心的参数是 $e^{-\lambda}$，所以我们的函数 $g(\lambda) = e^{-\lambda}$。这个函数的导数是 $g'(\lambda) = -e^{-\lambda}$。因此，根据delta方法，我们有：

$Var(g(\lambda)) \approx [g'(\mu)]^2 \sigma^2 = [-e^{-\mu}]^2 \sigma^2 = e^{-2\mu} \sigma^2$

在这里，$\mu$ 是 $\lambda$ 的真实值，$\sigma^2$ 是 $\lambda$ 的MLE的方差。在大样本下，$\lambda$ 的MLE的方差通常是 $\lambda^2/n$，其中 $n$ 是样本大小。因此，我们有：

$$Var(g(\lambda)) \approx e^{-2\mu} \lambda^2/n = \lambda^2 e^{-2\lambda}/n$$

这就是为什么选项C的方差与尾部概率 $e^{-\lambda}$ 的MLE的渐近分布匹配的原因。

## Question 3

Let $\hat{\gamma_n}$ be the maximum likelihood estimator for the parameter of the Pareto distribution with pdf

$$
f(x;\gamma) = \frac{\gamma}{(1+x)^{\gamma+1}}, \space x > 0
$$

Which of the following are true about $\hat{\gamma_n}$?

A. $\hat{\gamma_n}$ is asymptotically normal
B. $\lim_{n \to \infty} E[\hat{\gamma_n}] = \gamma$
C. $\hat{\gamma_n}$ is an unbiased estimator of $\gamma$
D. $\hat{\gamma_n}$ does not rely on the sample size $n$

这个问题涉及到Pareto分布的参数 $\gamma$ 的最大似然估计量（MLE） $\hat{\gamma}_n$ 的性质。下面是对每个选项的解释：

1. **$\hat{\gamma}_n$ 有渐近正态分布**：这是正确的。在大样本极限下，最大似然估计量的分布通常可以用正态分布来近似。这是由大数定律和中心极限定理保证的。

2. **$\lim_{n \to \infty} E[\hat{\gamma}_n] = \gamma$**：这是正确的。这个性质称为一致性。如果一个估计量是一致的，那么它的期望值会随着样本大小的增加而趋近于真实的参数值。在这个问题中，$\hat{\gamma}_n$ 是一致的，因此这个选项是正确的。

3. **$\hat{\gamma}_n$ 是 $\gamma$ 的无偏估计量**：这是错误的。无偏性是指估计量的期望值等于真实的参数值。然而，并不是所有的估计量都是无偏的。在这个问题中，$\hat{\gamma}_n$ 并不一定是无偏的。事实上，对于很多分布来说，最大似然估计量通常是有偏的。**我们通常说MLE是渐近无偏的**，即在样本大小趋于无穷时，MLE的偏差会趋于零。

4. **$\hat{\gamma}_n$ 不依赖于 $n$**：这是错误的。最大似然估计量通常是样本数据的函数，因此它通常会依赖于样本大小 $n$。在这个问题中，$\hat{\gamma}_n$ 显然是依赖于 $n$ 的，因为它是根据样本数据计算出来的。

所以，只有前两个选项是正确的，后两个选项是错误的。

## Question 4

Let $X_1, X_2, \ldots, X_n$ be a random sample from any distribution with mean $\mu$ and variance $\sigma^2$.
What is the asymptotic distribution of $\sum_{i=1}^n (X_i)$?

这个问题的答案应该是 $$N(n\mu, n\sigma^2)$$。

这是因为，根据中心极限定理，当样本量 $n$ 趋向于无穷大时，样本均值的分布将趋近于正态分布 $N(\mu, \sigma^2/n)$。然而，这个问题问的是样本总和 $\sum_{i=1}^{n}X_i$ 的渐近分布，而不是样本均值。

样本总和可以看作是 $n$ 个样本均值的和，因此其均值是 $n\mu$，方差是 $n\sigma^2$。所以，样本总和的渐近分布应该是 $$N(n\mu, n\sigma^2)$$。

## Question 5

Let $X_1, X_2, \ldots, X_n$ be a random sample from a distribution with pdf

$$
f(x;\theta) = \theta x^{\theta-1}I_{(0,1)}(x)
$$

To what does the sample mean $\bar{X}$ converge in probability?

这个问题涉及到随机样本 $X_1, X_2, ..., X_n$ 从概率密度函数 $f(x) = \theta x^{\theta - 1} I_{(0,1)}(x)$ 的分布中抽取，其中 $I_{(0,1)}(x)$ 是指示函数，当 $x$ 在区间 (0,1) 内时取值为1，否则为0。这实际上是一个参数为 $\theta$ 的Beta分布（Beta($\theta$, 1)）。

对于Beta分布，其期望值 $E[X]$ 是 $$\frac{\alpha}{\alpha + \beta}$$，其中 $\alpha$ 和 $\beta$ 是Beta分布的两个参数。在这个问题中，$\alpha = \theta$，$\beta = 1$，所以期望值是 $\frac{\theta}{\theta + 1}$。

因此，随着样本量 $n$ 的增加，样本均值 $\bar{X}$ 将以概率收敛于这个期望值。所以，答案是 $\frac{\theta}{\theta + 1}$。