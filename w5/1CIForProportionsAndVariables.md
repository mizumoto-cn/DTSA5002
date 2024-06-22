# Week5 Quiz1 CI for Proportions and Variables

> 总结：
> 1. 对于比例的置信区间，需要计算标准误差，然后计算置信区间。
>
> !!!
> 知识要点
> CI的标准计算方法：
> 1. 找出估计量
> 2. 找出估计量的渐近分布
> 3. 计算区间

## Question 1

Suppose 250 randomly selected people in a community are surveyed to determine whether or not they support a tax increase to fund community infrastructure. Of the 250 surveyed, 112 were in favor of the tax increase. 

Give a 95% confidence interval for the true proportion of people in the community who support the tax increase.

由题意可得：$n=250$, $\alpha=0.05$, $\hat p=\frac{112}{250}$。

se = $\sqrt{\frac{\hat p(1-\hat p)}{n}}$

第一步，确认$\hat p \pm 3se$的值域是否在0-1之间。

```r
n <- 250
p <- 112/250
alpha <- 0.05
se <- sqrt(p*(1-p)/n)
se
p + 3*se
p - 3*se
```

0.0314512956807824
0.542353887042347
0.353646112957653

第二步，计算置信区间。

```r
p + qnorm(1-alpha/2)*se
p - qnorm(1-alpha/2)*se
```

0.509643406801454
0.386356593198546

所以，95%的置信区间为(0.386356593198546, 0.509643406801454)。

## Question 2

A new shopping mall is proposed on unincorporated land on the boundary between two cities. A random sample of 150 residents from City A who live within within 1 mile of the boundary was taken. Of this sample, 78 were in favor of the mall. Similarly, a random sample of 150 residents from City B who live within 1 mile of the boundary was taken. Of this sample, 92 were in favor of the mall. 

Find a 95% confidence interval for $p_B - p_A$, where $p_A$ and $p_B$ are the true proportions of residents in City A and City B, respectively, who are in favor of the mall.

由题意可得：$n_A=150$, $n_B=150$, $\alpha=0.05$, $\hat p_A=\frac{78}{150}$, $\hat p_B=\frac{92}{150}$。

se = $\sqrt{\frac{\hat p_A(1-\hat p_A)}{n_A} + \frac{\hat p_B(1-\hat p_B)}{n_B}}$

```r
n_A <- 150
n_B <- 150
p_A <- 78/150
p_B <- 92/150
alpha <- 0.05
se <- sqrt(p_A*(1-p_A)/n_A + p_B*(1-p_B)/n_B)
se
p_B - p_A + qnorm(1-alpha/2)*se
p_B - p_A - qnorm(1-alpha/2)*se
```
0.0569652265600431
0.204983125762182
-0.0183164590955156

所以，95%的置信区间为(-0.0183164590955156, 0.204983125762182)。

## Question 3

Consider the following data set.

9.2229,8.3665,8.797058,10.2195,6.5629

Assuming that these data come from a normal distribution, find a 92% confidence interval for the true variance of that distribution. 

由题意可得：$n=5$, $\alpha=0.08$。

首先计算样本方差。

```r
data <- c(9.2229,8.3665,8.797058,10.2195,6.5629)
n <- length(data)
s2 <- var(data)
s2
```
1.8120531426328

已知$\frac{(n-1)s^2}{\sigma^2} \sim \chi^2(n-1)$，所以有：

$\frac{(n-1)s^2}{\chi^2_{1-\alpha/2}(n-1)} \leq \sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{\alpha/2}(n-1)}$

```r
alpha <- 0.08
s2 * (n-1) / qchisq(1-alpha/2, n-1)
s2 * (n-1) / qchisq(alpha/2, n-1)
```

0.722976273183767
11.5574718975411

所以，92%的置信区间为(0.722976273183767, 11.5574718975411)。

## Question 4

Which of the following are true about a confidence interval for a normal population variance? 

(Select all that apply.)


The confidence interval may be infinite.

The confidence interval must include the sample variance $S^2$.

A 95% confidence interval for the variance must fully contain any 90% confidence interval for the variance.

A 90% confidence interval will be wider than a 95% confidence interval.

Here are the correct statements about a confidence interval for a normal population variance:

1. **The confidence interval may be infinite.** This is **True**. The confidence interval for a variance can indeed be infinite, especially when dealing with small sample sizes.

2. **The confidence interval must include the sample variance $S^2$.** This is **True**. The confidence interval for the variance must include the sample variance $S^2$ because the sample variance is an estimate of the population variance. Therefore, the confidence interval must include the sample variance.

3. **A 95% confidence interval for the variance must fully contain any 90% confidence interval for the variance.** This is false. A 95% confidence interval for the variance does not have to fully contain any 90% confidence interval for the variance. The two intervals are independent of each other and can overlap or not overlap.

4. **A 90% confidence interval will be wider than a 95% confidence interval.** This is false. A 95% confidence interval will be wider than a 90% confidence interval because the higher the confidence level, the wider the confidence interval. This is because a higher confidence level means that we want to be more sure that we are capturing the true population parameter, which requires a wider interval.