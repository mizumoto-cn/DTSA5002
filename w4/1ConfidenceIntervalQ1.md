# Week4 Quiz1 Confidence Interval Q1

> !!!!
> 观察第1,2题目，第1题是小样本，第2题是大样本，所以这里分别计算。
> 第1题：样本量为5，所以用t分布计算。$$\bar{x} \pm qt(1-\frac{\alpha}{2}, n-1) se = \bar{x} \pm t_{{\alpha/2},{n-1}} \frac{s}{\sqrt{n}}$$
> 第2题：样本量为138，所以用z分布计算。$$ \bar{x} \pm qnorm(1-\frac{\alpha}{2}) se = \bar{x} \pm z_{\alpha/2} \frac{s}{\sqrt{n}}$$
> 其中se为标准误差，为样本标准差除以样本量的平方根：
> $$se = \frac{s}{\sqrt{n}}$$

> !!!!
> 在一些问题（如题4题5）中，已知的是总体方差σ²，所以在计算标准误差时，我们应该使用总体标准差（σ），而不是样本标准差（s）。因此，我们应该使用z分布而不是t分布。

## Question 1

Sample: 2781 2900 3013 2856 2888
Preliminary investigation of the data support the assumption that viscosity is at least approximately normally distributed.

Give a 95% confidence interval for true average viscosity.

```{r}
data = c(2781,2900,3013,2856,2888)
mean = mean(data)

sd = sd(data)
n = 5
se = sd/sqrt(n)

z = qt(0.975, 4)
ub = mean + z*se
lb = mean - z*se
```

已知样本均值为2887.6，样本标准差为78.8，样本量为5，置信水平为95%，查t分布表得t=2.776。

**容量小于30，用t分布**，所以计算过程为：

**$$\bar{x} \pm t_{{\alpha/2},{n-1}} \frac{s}{\sqrt{n}}$$**

所以，95%的置信区间为：
$$(2783.26844830561, 2991.93155169439)$$

## 2

The NIST Standard Reference Database gave the following summary informationfor fracture strengths (MPa) of 138 ceramic bars fired in a particular kiln:

$$\bar{x} = 83.14, s = 2.73$$

Calculate an approximate  90\% confidence interval for true average fracture strength.

已知 $\bar{x} = 83.14, s = 2.73$，样本量为138，置信水平为90%，即$\alpha = 0.1$。

**容量大于30，用z分布**，所以计算过程为：

$$\bar{x} \pm z_{\alpha/2} \frac{s}{\sqrt{n}}$$

```{r}
mean = 83.14
sd = 2.73
n = 138
se = sd/sqrt(n)

z = qnorm(0.95)
ub = mean + z*se
lb = mean - z*se
```

83.5222525230391
82.7577474769609

所以，90%的置信区间为：
$$(82.7577474769609, 83.5222525230391)$$

## 3

Suppose that a random sample of 42 bottles of a particular brand of wine is selected and the alcohol content of each bottle is determined.
Let $\mu$ denote the average alcohol content for the population of all bottles of the brand under study. Suppose that the resulting 95% confidence interval is $(10.8, 12.4)$.

Which of the following is true when using the same data set. (Select all that apply.)

A A 90% confidence interval for μ will be an interval that is contained in the interval $(10.8, 12.4)$.

B A 90% confidence interval for μ will be an interval that contains the interval $(10.8, 12.4)$.

C A 90% confidence interval will end up being narrower.

D The true mean $\mu$ is between 10.8 and 12.4 90% of the time.

对于这个问题，以下是正确的选项：

**A.** 90%置信区间对于 $\mu$ 将会是一个包含在区间 $(10.8, 12.4)$ 内的区间。

**C.** 90%置信区间将会更窄。

解释如下：

- **选项A**：一个90%置信区间将会比95%置信区间更窄，因为我们对参数的估计不那么确定。因此，90%置信区间将会被包含在95%置信区间 $(10.8, 12.4)$ 内。

- **选项C**：如上所述，一个90%置信区间将会比95%置信区间更窄，因为我们对参数的估计不那么确定。

- **选项B**：这是错误的，因为90%置信区间将会比95%置信区间更窄，而不是更宽。

- **选项D**：这是错误的，因为置信区间并不能告诉我们真实的均值 $\mu$ 有90%的概率落在 $(10.8, 12.4)$ 这个区间内。置信区间是关于我们的估计的不确定性的度量，而不是关于参数本身的不确定性的度量。

## 4

The lengths, in inches for a particular population of sockeye salmon (Oncorhynchus nerka) are known to be normally distributed with variance $\sigma^2 = 25.1$. A random sample of 12 sockeye salmon were pulled from the region and measured, producing a sample mean of $\bar{x} = 23.7$ inches.

Derive an 80% confidence interval for the true population mean length $\mu$.

已知 $\sigma^2 = 25.1$，样本均值 $\bar{x} = 23.7$，样本量为12，置信水平为80%，即 $\alpha = 0.2$。

正确解法：

已知总体方差 $\sigma^2 = 25.1$，所以在计算标准误差时，我们应该使用总体标准差 $\sigma$，而不是样本标准差 $s$。因此，我们应该使用z分布而不是t分布。所以计算过程为：

$$\bar{x} \pm z_{\alpha/2} \frac{\sigma}{\sqrt{n}}$$

```{r}
mean = 23.7
n = 12
s2 = 25.1
alpha = 0.2
se = sqrt(s2/n)
z = qnorm(1-alpha/2)
ub = mean + z*se
lb = mean - z*se
```

25.5534561819355
21.8465438180645

所以，80%的置信区间为： $(21.8465438180645, 25.5534561819355)$

> 错误解法！！！
> 您的计算过程看起来是正确的，但是我注意到您使用的是样本方差（s²）而不是总体方差（σ²）。在这个问题中，已知的是总体方差（σ² = 25.1），所以在计算标准误差时，我们应该使用总体标准差（σ），而不是样本标准差（s）。因此，我们应该使用z分布而不是t分布。
> 所以，计算过程应该为：
> $$\bar{x} \pm z_{\alpha/2} \frac{\sigma}{\sqrt{n}}$$
> 其中，z是标准正态分布的分位数。这可能解释了您的答案与正确答案之间的差异。希望这个解释对您有所帮助！

<del>
容量小于30，用t分布，所以计算过程为：

$$\bar{x} \pm t_{{\alpha/2},{n-1}} \frac{s}{\sqrt{n}} = \bar{x} \pm qt(1-\frac{\alpha}{2}, n-1) \sqrt{\frac{\sigma^2}{n}}$$

```{r}
mean = 23.7
n = 12
s2 = 25.1
alpha = 0.2

se = sqrt(s2/n)
t = qt(1-alpha/2, n-1)
ub = mean + t*se
lb = mean - t*se
```

25.6718741090996
21.7281258909004

所以，80%的置信区间为：(21.7281258909004, 25.6718741090996)
</del>

## 5

You are planning on taking a random sample from a normal distribution with variance
9  and making a 95% confidence interval for its mean 𝜇.

What is the minimum sample size necessary to ensure that the length of this confidence interval is less than 2.7?

```{r}
l = 22
n =16
cal <- function(n) 2*qnorm(.975)*sqrt(9/n)
while(l>=2.7){
    n=n+1
    l = cal(n)
    print(l)
}
n
```

[1] 2.852167
[1] 2.771808
[1] 2.697879
19
