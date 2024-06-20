# W2 Quiz2 Invariance, Mean-Squared Error, and Efficiency

## Question 1

Suppose that $X_1, X_2, ..., X_n$ is a random sample from the exponential distribution with parameter $\lambda$. 
Find the MLE for P(X > 1) where X is a future sampled value.

对于指数分布，我们知道其概率密度函数（PDF）为：

$
f(x;\lambda) = \lambda e^{-\lambda x}, \quad x \geq 0
$

并且，我们知道 $\lambda$ 的最大似然估计是 $\hat{\lambda} = n / \sum_{i=1}^{n} X_i$。

现在，我们要找的是 $P(X > 1)$ 的最大似然估计。由于 $X$ 是指数分布，我们有：

$
P(X > 1) = \int_{1}^{\infty} \lambda e^{-\lambda x} dx = e^{-\lambda}
$

因此，$P(X > 1)$ 的最大似然估计就是将 $\lambda$ 的最大似然估计代入上式，得到：

$
\hat{P}(X > 1) = e^{-\hat{\lambda}} = e^{-n / \sum_{i=1}^{n} X_i}
$

所以，对于指数分布，$P(X > 1)$ 的最大似然估计是 $e^{-n / \sum_{i=1}^{n} X_i}$。

即 $\boxed{e^{-1 / \bar{X}}}$。

## Question 2

效率是一个衡量估计量质量的指标，定义为两个无偏估计量的方差之比。在这个问题中，我们需要找到 $\hat{\mu}_1$ 相对于 $\hat{\mu}_2$ 的效率。

首先，我们知道样本均值 $\hat{\mu}_1 = \bar{X}$ 的方差是 $Var(\hat{\mu}_1) = Var(\bar{X}) = \frac{\sigma^2}{n}$。

然后，我们需要找到 $\hat{\mu}_2$ 的方差。注意到 $\hat{\mu}_2$ 是 $X_1$ 和 $\bar{X}_{(2:n)}$（即去掉第一个观测值后的样本均值）的加权平均，我们有：

$
Var(\hat{\mu}_2) = Var\left(\frac{X_1}{3} + \frac{2}{3(n-1)}\sum_{i=2}^{n}X_i\right)
$

由于各个 $X_i$ 是独立同分布的，我们可以将方差分解为各部分的和，得到：

$
Var(\hat{\mu}_2) = \frac{1}{9}Var(X_1) + \frac{4}{9(n-1)^2}\sum_{i=2}^{n}Var(X_i) = \frac{1}{9}\sigma^2 + \frac{4}{9(n-1)}\sigma^2
$

因此，$\hat{\mu}_1$ 相对于 $\hat{\mu}_2$ 的效率为：

$
Eff(\hat{\mu}_1, \hat{\mu}_2) = \frac{Var(\hat{\mu}_2)}{Var(\hat{\mu}_1)} = \frac{\frac{1}{9}\sigma^2 + \frac{4}{9(n-1)}\sigma^2}{\frac{\sigma^2}{n}} = \frac{n}{9} + \frac{4n}{9(n-1)} = \frac{n^2 - n + 4n}{9(n-1)} = \frac{n^2 + 3n}{9(n-1)} = \frac{n(n+3)}{9(n-1)}
$

这就是 $\hat{\mu}_1$ 相对于 $\hat{\mu}_2$ 的效率。

## Question 3

偏差是估计量的期望值与真实参数值之间的差。在这个问题中，我们需要找到估计量 $\hat{\sigma}^2$ 的偏差。

首先，我们知道样本方差的期望值是：

$
E\left[\frac{1}{n}\sum_{i=1}^{n}(X_i - \bar{X})^2\right] = \frac{n-1}{n}\sigma^2
$

这是因为 $\sum_{i=1}^{n}(X_i - \bar{X})^2 / n$ 是样本方差的无偏估计量，其期望值等于总体方差 $\sigma^2$。

然后，我们可以计算估计量 $\hat{\sigma}^2$ 的偏差，即：

$
Bias(\hat{\sigma}^2) = E[\hat{\sigma}^2] - \sigma^2 = \frac{n-1}{n}\sigma^2 - \sigma^2 = -\frac{1}{n}\sigma^2
$

所以，对于这个问题，估计量 $\hat{\sigma}^2$ 的偏差是 $-\frac{1}{n}\sigma^2$。

## Question 4

对于这个问题，我们首先需要找到这个分布的累积分布函数（CDF），然后设定它等于0.5来找到中位数。对于给定的概率密度函数（PDF）：

$
f(x) = 
\begin{cases} 
\frac{3x^2}{\theta^3}, & 0 < x < \theta \\
0, & \text{otherwise}
\end{cases}
$

我们可以积分得到累积分布函数（CDF）：

$
F(x) = \int_0^x f(t) dt = \int_0^x \frac{3t^2}{\theta^3} dt = \frac{x^3}{\theta^3}
$

然后，我们设定 $F(x) = 0.5$ 来找到中位数 $\xi$：

$
0.5 = \frac{\xi^3}{\theta^3} \Rightarrow \xi = \theta \cdot 0.5^{1/3}
$

所以，对于这个分布，中位数 $\xi$ 是 $\theta \cdot 0.5^{1/3}$。

现在，如果我们有一个随机样本 $X_1, X_2, ..., X_n$，那么 $\theta$ 的最大似然估计是样本的最大值，即 $\hat{\theta} = \max(X_1, X_2, ..., X_n)$。因此，中位数 $\xi$ 的最大似然估计就是将 $\theta$ 的最大似然估计代入上式，得到：

$
\hat{\xi} = \hat{\theta} \cdot 0.5^{1/3} = \max(X_1, X_2, ..., X_n) \cdot 0.5^{1/3}
$

所以，对于这个分布，中位数 $\xi$ 的最大似然估计是 $\max(X_1, X_2, ..., X_n) \cdot 0.5^{1/3}$。

## Question 5

均方误差（MSE）是一个估计量的期望值与真实参数值之间差的平方的期望值。对于泊松分布，参数 $\lambda$ 的最大似然估计是样本均值 $\bar{X}$。所以，我们有 $\hat{\lambda} = \bar{X}$。

我们知道，对于泊松分布，其均值和方差都等于 $\lambda$。因此，样本均值 $\bar{X}$ 的期望值是 $\lambda$，方差是 $\lambda/n$。

因此，我们可以计算 $\hat{\lambda}$ 的均方误差（MSE）：

$
MSE(\hat{\lambda}) = Bias(\hat{\lambda})^2 + Var(\hat{\lambda})
$

由于 $\hat{\lambda}$ 是无偏的（即，Bias($\hat{\lambda}$) = 0），我们有：

$
MSE(\hat{\lambda}) = Var(\hat{\lambda}) = \frac{\lambda}{n}
$

所以，对于这个问题，$\hat{\lambda}$ 作为 $\lambda$ 的估计量的均方误差是 $\frac{\lambda}{n}$。
