# w2 q1 MLEs

## 知识要点

> MLE计算方法：
>
> 1. 计算似然函数：$L(\theta; x) = \prod_{i=1}^{n} f(x_i; \theta)$
> 2. 计算对数似然函数：$l(\theta; x) = \log(L(\theta; x))$
> 3. 对对数似然函数求导：$\frac{d}{d\theta} l(\theta; x) = 0$
> 4. 解方程得到 $\theta$ 的估计值
>
> 特殊情况：似然函数递增或递减，直接取令似然函数最大的值

## Question 1

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the Poisson distribution with parameter 𝜆. 

What is the maximum likelihood estimator for 𝜆?

对于泊松分布，参数 $\lambda$ 的最大似然估计是样本均值 $\bar{X}$。所以答案是样本均值 $\bar{X}$。
泊松分布概率质量函数（PMF）为：

$$
P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}
$$

其中，$\lambda$ 是平均发生率，$k$ 是实际发生的次数。

如果我们有一个样本 $X_1, X_2, ..., X_n$，那么似然函数就是所有样本点的概率的乘积，即：

$$
L(\lambda; x) = \prod_{i=1}^{n} P(X = x_i)
$$

将 PMF 代入似然函数，我们得到：

$$
L(\lambda; x) = \prod_{i=1}^{n} \frac{\lambda^{x_i} e^{-\lambda}}{x_i!}
$$

为了简化计算，我们通常取对数似然函数，即：

$$
l(\lambda; x) = \log(L(\lambda; x)) = \sum_{i=1}^{n} [x_i \log(\lambda) - \lambda - \log(x_i!)]
$$

为了找到 $\lambda$ 的最大似然估计，我们对 $\lambda$ 求导，并令其等于零，得到：

$$
\frac{d}{d\lambda} l(\lambda; x) = \sum_{i=1}^{n} [\frac{x_i}{\lambda} - 1] = 0
$$

解这个方程，我们得到 $\lambda$ 的最大似然估计为样本均值 $\bar{X}$，即：

$$
\hat{\lambda} = \frac{1}{n} \sum_{i=1}^{n} x_i = \bar{X}
$$

所以，对于泊松分布，参数 $\lambda$ 的最大似然估计是样本均值 $\bar{X}$。

## Question 2

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the $$\Gamma(\alpha, \beta)$$, where $\alpha$ is known.

对于伽玛分布 $\Gamma(\alpha, \beta)$，其中 $\alpha$ 已知，参数 $\beta$ 的最大似然估计是 $\alpha / \bar{X}$。所以答案是 $\alpha / \bar{X}$。

这是因为伽玛分布的概率密度函数（PDF）为：

$$
f(x;\alpha,\beta) = \frac{1}{\beta^\alpha \Gamma(\alpha)} x^{\alpha-1} e^{-x/\beta}
$$

其中，$\Gamma(\alpha)$ 是伽马函数，$\alpha$ 和 $\beta$ 是伽玛分布的形状参数和尺度参数。

如果我们有一个样本 $X_1, X_2, ..., X_n$，那么似然函数就是所有样本点的概率的乘积，即：

$
L(\beta; x) = \prod_{i=1}^{n} f(x_i;\alpha,\beta)
$

将 PDF 代入似然函数，我们得到：

$$
L(\beta; x) = \prod_{i=1}^{n} \frac{1}{\beta^\alpha \Gamma(\alpha)} x_i^{\alpha-1} e^{-x_i/\beta}
$$

为了简化计算，我们通常取对数似然函数，即：

$$
l(\beta; x) = \log(L(\beta; x)) = \sum_{i=1}^{n} [(\alpha-1) \log(x_i) - x_i/\beta - \alpha \log(\beta) - \log(\Gamma(\alpha))]
$$

为了找到 $\beta$ 的最大似然估计，我们对 $\beta$ 求导，并令其等于零，得到：

$$
\frac{d}{d\beta} l(\beta; x) = \sum_{i=1}^{n} [-x_i/\beta^2 - \alpha/\beta] = 0
$$

解这个方程，我们得到 $\beta$ 的最大似然估计为 $\alpha / \bar{X}$，即：

$$
\hat{\beta} = \frac{\alpha}{\bar{X}} = \frac{\alpha}{\frac{1}{n} \sum_{i=1}^{n} x_i}
$$

所以，对于伽玛分布，已知 $\alpha$ 时，参数 $\beta$ 的最大似然估计是 $$\alpha / \bar{X}$$。

## Question 3

Consider a random sample 𝑋1,𝑋2,…,𝑋𝑛 from the shifted exponential distribution with pdf

$$
f(x; \theta) = e^{-(x-\theta)} \text{ for } x > \theta \text{ and } 0 \text{ otherwise}
$$

What is the maximum likelihood estimator for 𝜃 ?

对于平移指数分布，参数 $\theta$ 的最大似然估计是样本的最小值，即 $\min(X_1, X_2, ..., X_n)$。所以，对于你的问题，答案是 $\min(X_1, X_2, ..., X_n)$。

这是因为平移指数分布的概率密度函数（PDF）为：

$
f(x;\theta) = 
\begin{cases} 
e^{-(x-\theta)}, & x \geq \theta \\
0, & x < \theta 
\end{cases}
$

如果我们有一个样本 $X_1, X_2, ..., X_n$，那么似然函数就是所有样本点的概率的乘积，即：

$
L(\theta; x) = \prod_{i=1}^{n} f(x_i;\theta)
$

由于 $x_i \geq \theta$，我们可以将 PDF 代入似然函数，得到：

$
L(\theta; x) = \prod_{i=1}^{n} e^{-(x_i-\theta)} = e^{-\sum_{i=1}^{n}(x_i-\theta)}
$

为了找到 $\theta$ 的最大似然估计，我们需要最大化似然函数。但是，由于 $-\sum_{i=1}^{n}(x_i-\theta)$ 是 $\theta$ 的递减函数，似然函数是 $\theta$ 的递增函数。因此，为了最大化似然函数，我们需要最小化 $\theta$，即取样本中的最小值。

所以，对于平移指数分布，参数 $\theta$ 的最大似然估计是样本的最小值 $\min(X_1, X_2, ..., X_n)$。

## Question 4

Question 4
Consider a random sample $X_1, X_2, ..., X_n$ from the continuous Pareto distribution with pdf

$$
f(x; \gamma) = \frac{\gamma}{(1+x)^{\gamma+1}} \text{ for } x \geq 1 \text{ and } 0 \text{ otherwise}
$$

Here $\gamma > 0$ is the parameter of the distribution. What is the maximum likelihood estimator of the parameter $\gamma$?

对于连续的Pareto分布，参数 $\gamma$ 的最大似然估计是 $n / \sum_{i=1}^{n} \ln(1+X_i)$。所以，对于你的问题，答案是 $n / \sum_{i=1}^{n} \ln(1+X_i)$。

这是因为Pareto分布的概率密度函数（PDF）为：

$
f(x;\gamma) = 
\begin{cases} 
\gamma (1+x)^{-\gamma-1}, & x \geq 0 \\
0, & x < 0 
\end{cases}
$

如果我们有一个样本 $X_1, X_2, ..., X_n$，那么似然函数就是所有样本点的概率的乘积，即：

$
L(\gamma; x) = \prod_{i=1}^{n} f(x_i;\gamma)
$

将 PDF 代入似然函数，我们得到：

$
L(\gamma; x) = \prod_{i=1}^{n} \gamma (1+x_i)^{-\gamma-1} = \gamma^n \prod_{i=1}^{n} (1+x_i)^{-\gamma-1}
$

为了简化计算，我们通常取对数似然函数，即：

$
l(\gamma; x) = \log(L(\gamma; x)) = n \log(\gamma) - (\gamma+1) \sum_{i=1}^{n} \log(1+x_i)
$

为了找到 $\gamma$ 的最大似然估计，我们对 $\gamma$ 求导，并令其等于零，得到：

$
\frac{d}{d\gamma} l(\gamma; x) = \frac{n}{\gamma} - \sum_{i=1}^{n} \log(1+x_i) = 0
$

解这个方程，我们得到 $\gamma$ 的最大似然估计为 $n / \sum_{i=1}^{n} \ln(1+X_i)$，即：

$
\hat{\gamma} = \frac{n}{\sum_{i=1}^{n} \ln(1+X_i)}
$

所以，对于连续的Pareto分布，参数 $\gamma$ 的最大似然估计是 $n / \sum_{i=1}^{n} \ln(1+X_i)$。

## Question 5

Consider a random sample 𝑋1,𝑋2,…,𝑋𝑛 from the shifted exponential distribution  with rate 
𝜆 with pdf

$$
f(x; \lambda,\theta) = \lambda e^{-\lambda(x-\theta)} \text{ for } x > \theta \text{ and } 0 \text{ otherwise}
$$

What are the maximum likelihood estimator for 𝜆 and 𝜃?

对于平移指数分布，参数 $$\theta$$ 的最大似然估计是样本的最小值，即 $$\min(X_1, X_2, ..., X_n)$$。参数 $$\lambda$$ 的最大似然估计是 $$n / \sum_{i=1}^{n} (X_i - \theta)$$，其中 $$\theta$$ 是样本的最小值。

这是因为平移指数分布的概率密度函数（PDF）为：

$$
f(x;\lambda,\theta) = 
\begin{cases} 
\lambda e^{-\lambda(x-\theta)}, & x \geq \theta \\
0, & x < \theta 
\end{cases}
$$

如果我们有一个样本 $X_1, X_2, ..., X_n$，那么似然函数就是所有样本点的概率的乘积，即：

$
L(\lambda, \theta; x) = \prod_{i=1}^{n} f(x_i;\lambda,\theta)
$

将 PDF 代入似然函数，我们得到：

$$
L(\lambda, \theta; x) = \prod_{i=1}^{n} \lambda e^{-\lambda(x_i-\theta)} = \lambda^n e^{-\lambda \sum_{i=1}^{n}(x_i-\theta)}
$$

为了找到 $\lambda$ 和 $\theta$ 的最大似然估计，我们需要最大化似然函数。首先，我们注意到 $\theta \leq x_i$ 对所有的 $i$，所以 $\theta$ 的最大似然估计是样本的最小值，即 $\hat{\theta} = \min(X_1, X_2, ..., X_n)$。

然后，我们取对数，并对 $\lambda$ 求导，并令其等于零，得到：

$$
l(\lambda, \theta; x) = \log(L(\lambda, \theta; x)) = n \log(\lambda) - \lambda \sum_{i=1}^{n}(x_i-\theta)
$$

$$
\frac{d}{d\lambda} l(\lambda, \theta; x) = n/\lambda - \sum_{i=1}^{n}(x_i-\theta) = 0
$$

解这个方程，我们得到 $\lambda$ 的最大似然估计为 $n / \sum_{i=1}^{n} (X_i - \theta)$，即：

$$
\hat{\lambda} = \frac{n}{\sum_{i=1}^{n} (X_i - \hat{\theta})}
$$

所以，对于平移指数分布，参数 $\lambda$ 的最大似然估计是 $n / \sum_{i=1}^{n} (X_i - \theta)$，参数 $\theta$ 的最大似然估计是样本的最小值 $$\min(X_1, X_2, ..., X_n)$$。
