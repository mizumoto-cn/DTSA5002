# Week 5 Quiz2 Non-Normal Confidence Intervals

## 知识要点

> 指数、Gamma、Chi-Square分布之间的关系与转变
> 指数分布转换为Gamma分布: $exp(\lambda) = \Gamma(1, \lambda)$
> Gamma分布转换为Chi-Square分布: 如果$X \sim \Gamma(k, \beta)$，那么$2\beta X \sim \chi^2(2k)$

## Question 1

Let $X_1, X_2, \ldots, X_n$ be a random sample from a continuous uniform distribution on the interval $[0, \theta]$, where $\theta > 0$.

Using the "cdf method" from this lesson, we can show that $Y = \max(X_1, X_2, \ldots, X_n)$ has pdf given by

$$f(y, \theta) = \frac{n}{\theta^n} y^{n-1}, \quad 0 \le y \le \theta.$$

Which of the following is a valid $100(1-\alpha)\%$ confidence interval for $\theta$?

A $(\frac{Y_n}{(1-\alpha)^{1/n}}, \infty)$

B $(0, \frac{Y_n}{(1-\alpha)^{1/n}})$

C $(\frac{Y_n}{\alpha^{1/n}}, \infty)$

D $(0, \frac{Y_n}{\alpha^n})$

The correct answer is **A**. 

The $100(1-\alpha)\%$ confidence interval for $\theta$ is given by $$\left(\frac{Y_n}{(1-\alpha)^{1/n}}, \infty\right)$$

This is because the maximum of a sample from a uniform distribution is a sufficient statistic for $\theta$. The distribution of $Y_n = \max(X_1, X_2, \ldots, X_n)$ is given by $F_Y(y) = \left(\frac{y}{\theta}\right)^n$, for $0 \le y \le \theta$. 

So, the $100(1-\alpha)\%$ upper confidence limit for $\theta$ is the $100\alpha\%$ percentile of the distribution of $Y_n$, which is $\frac{Y_n}{(1-\alpha)^{1/n}}$. Hence, the $100(1-\alpha)\%$ confidence interval for $\theta$ is $\left(\frac{Y_n}{(1-\alpha)^{1/n}}, \infty\right)$. 

The other options **B**, **C**, and **D** are not correct.

## Question 2

Let $X_1, X_2, \ldots, X_n$ be a random sample from the shifted continuous exponential distribution with rate 1 and pdf

$$f(x, \theta) = e^{-(x-\theta)}, \quad x > \theta.$$

Which of the following is a valid 95% confidence interval for $\theta$  based on the minimum value $Y_n = \min(X_1, X_2, \ldots, X_n)$?

$(Y_n + \frac{ln 0.05}{n}, Y_n)$

对于这个问题，我们应该使用指数分布的性质来找到一个有效的95%置信区间。对于指数分布，我们知道其累积分布函数（CDF）为：

$$F(x) = 1 - e^{-(x-\theta)}, \quad x > \theta.$$

因此，对于最小值$Y_n = \min(X_1, X_2, \ldots, X_n)$，其分布函数为：

$$F_{Y_n}(y) = 1 - (1 - F(y))^n = 1 - e^{-n(y-\theta)}, \quad y > \theta.$$

所以，pdf为：

$$f(y, \theta) = n e^{-n(y-\theta)}, \quad y > \theta.$$

这意味着$n(Y_n - \theta)$的分布为 $$n(Y_n - \theta) \sim \text{Gamma}(1, 1) \sim \text{Exp}(1)$$。

最后，我们知道指数分布的第$p$百分位数为$-\log(1-p)$。所以，对于$p = 0.95$，我们有 $$q_{\text{exp}}(0.95) = -\log(1 - 0.95) = -\log(0.05)$$。

唯一符合这个条件的选项是$(Y_n + \frac{\ln 0.05}{n}, Y_n)$，所以正确答案是$(Y_n + \frac{\ln 0.05}{n}, Y_n)$。

## Question 3

Let $X_1$ be a random sample of size 1 from the $\Gamma(3,\beta)$ distribution with parameter $\beta > 0$.

Derive a 90% confidence interval for $\beta$ based on the single observation $X_1$

(Yes, a sample of size 1 is silly but it makes for an easier computation and the point of this problem is to test the techniques for developing confidence intervals!)


$(0, \frac{\chi^2_{{0.10},6}}{2X_1})$

对于这个问题，我们应该使用伽马分布的性质来找到一个有效的90%置信区间。对于伽马分布，我们知道其形状参数为$k$，尺度参数为$\beta$，其概率密度函数（PDF）为：

$$f(x) = \frac{1}{\Gamma(k)\beta^k}x^{k-1}e^{-x/\beta}, \quad x > 0.$$

在这里，我们的$k = 3$，所以我们有 $X_1 \sim \Gamma(3, \beta)$。

对于单个观察值$X_1$，我们知道其期望值为$E[X_1] = k\beta = 3\beta$，方差为$Var[X_1] = k\beta^2 = 3\beta^2$。

因此，我们可以使用样本均值$\bar{X} = X_1$来估计$\beta$，即$\hat{\beta} = \frac{\bar{X}}{3}$。

然后，我们可以使用$\chi^2$分布的性质来构造置信区间。我们知道，如果$Z \sim \Gamma(k, \beta)$，那么$2\beta Z \sim \chi^2(2k)$。因此，对于$Z = X_1$，我们有$2\hat{\beta}X_1 = 2\frac{X_1^2}{3} \sim \chi^2(6)$。

对于$\alpha = 0.1$，我们有90%的置信区间为：

$$\left(0, \frac{\chi^2_{0.10}(6)}{2X_1}\right).$$

这就是$\beta$的有效90%置信区间。


