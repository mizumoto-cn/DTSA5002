# Week4 Quiz2 Confidence Interval For Difference Between Population Means

## 知识点

> - 两个总体均值之差的置信区间
> 大样本或分布方差已知时，用z分布；小样本且分布方差未知时，用t分布。
> 公式为：
> $$\bar{x}_1 - \bar{x}_2 \pm z_{\alpha/2} \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$$
> 或
> $$\bar{x}_1 - \bar{x}_2 \pm t_{\alpha/2, n_1+n_2-2} \sqrt{sp^2(\frac{1}{n_1} + \frac{1}{n_2})}$$
> 其中，$$sp^2 = \frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1+n_2-2}$$

## Question 1

A random sample of size 10 from the laminate system produced a sample mean warpage of 2.7 degrees and a random sample of size 12 from the hardwood flooring gave a sample mean warpage of 3.2 degrees. It is believed that both systems have a true warpage variance of 0.8 degrees squared.

Assuming warpage for both products are normally distributed, find a 90% confidence interval for 𝜇1−𝜇2 where 𝜇1 is the true mean warpage for laminate and 𝜇2 is the true mean warpage for hardwood.

```r
n1 = 10
mean1 = 2.7
s1 = sqrt(0.8)
n2 = 12
mean2 = 3.2
s2 = sqrt(0.8)
alpha = 0.1

se = sqrt(s1^2/n1 + s2^2/n2)
z = qnorm(1-alpha/2)

ub = mean1 - mean2 + z*se
lb = mean1 - mean2 - z*se
```

0.129930980293868
-1.12993098029387

So, the 90% confidence interval for 𝜇1−𝜇2 is (-1.12993098029387, 0.129930980293868).

> 注意：这是一个小样本问题，但是我们知道分布方差，所以我们使用z分布而不是t分布。

## Question 2

A random sample of size 10 from the laminate system produced a sample mean warpage of 2.7 degrees and a sample variance of 0.73. A random sample of size  12 from the hardwood flooring gave a sample mean warpage of 3.2 degrees and a sample variance of 0.80. It is believed that the true variance for the laminate system is the same as the true variance for the hardwood system.

Assuming warpage for both products are normally distributed, find a 90% confidence interval for 𝜇1−𝜇2 where 𝜇1 is the true mean warpage for laminate and 𝜇2 is the true mean warpage for hardwood.

> 注意：这是一个小样本问题，我们不知道分布方差，所以我们使用t分布。

```r
n1 = 10
mean1 = 2.7
s1 = sqrt(0.73)
n2 = 12
mean2 = 3.2
s2 = sqrt(0.8)
alpha = 0.1

sp2 = ((n1-1)*s1^2 + (n2-1)*s2^2)/(n1+n2-2)
se = sqrt(sp2*(1/n1 + 1/n2))
t = qt(1-alpha/2, n1+n2-2)

ub = mean1 - mean2 + t*se
lb = mean1 - mean2 - t*se
```

0.147382283805712
-1.14738228380571

So, the 90% confidence interval for 𝜇1−𝜇2 is (-1.14738228380571, 0.147382283805712).

## Question 3

The Slant Shear Test (SST) is a widely used test for evaluating the bond of resinous repair materials to concrete. It was applied to two random samples of concrete slabs which were finshed in different ways. Population 1 has a smooth finish while Population 2  has a more textured finish.

The sample mean shear strength ( in $N/mm^2$) and sample variance for the smooth finish sample of size 138 from were 18.17 and 1.78, respectively. The sample mean and variance in shear strength for a random sample of size 110 hand-chiseled specimens, were were 21.66 and 3.21.

Find a 95% confidence interval $\mu_1 - \mu_2$ for the difference in mean shear strengths between the two populations.

> 样本大小为138和110，所以这是一个大样本问题。尝试使用z分布。

```r
n1 = 138
mean1 = 18.17
s1 = sqrt(1.78)
n2 = 110
mean2 = 21.66
s2 = sqrt(3.21)
alpha = 0.05

se = sqrt(s1^2/n1 + s2^2/n2)
z = qnorm(1-alpha/2)

ub = mean1 - mean2 + z*se
lb = mean1 - mean2 - z*se
```

-3.08794278477589
-3.89205721522411

So, the 95% confidence interval for $\mu_1 - \mu_2$ is (-3.89205721522411, -3.08794278477589).
