# Week3 Quiz1 CRLB

## 知识要点

> 1. 克拉默-劳下界是一个用于评估无偏估计量方差的下限的工具。他的计算公式是：$Var(\hat{\tau(\theta)}) \geq \frac{[\tau'(\theta)]}{I_n(\theta)}$，其中，$\hat{\tau(\theta)}$ 是参数 $\tau(\theta)$ 的无偏估计量，$I(\theta)$ 是费舍尔信息。
> 2. 费舍尔信息的计算方式有几种，最基础的是：
> 2.1. 先根据分布的pdf $f(x;\theta)$ 计算对数似然函数的导数；得出 $f(\vec{x};\theta)$
> 2.2. 再对其取对数并求导，平方后代入得到费舍尔信息 $I_n(\theta)=E[(\frac{\partial}{\partial \theta} ln f(\vec{x};\theta))^2]$
>
> 3. 但是我们可以做如下简化：
> 3.1. $E[\frac{\partial}{\partial \theta} ln f(x;\theta)] = 0$，所以 $I_n(\theta) = -E[\frac{\partial^2}{\partial \theta^2} ln f(x;\theta)]$，即对对数似然函数求二阶导数的期望值的负数。
> 3.2. $I_n(\theta) = n\dot{I_1(\theta)}$，即单个观测的费舍尔信息的n倍。
>

## 1

Let $X_1, X_2, \ldots, X_n$ be a random sample from a Normal distribution with mean $\mu$ and variance $\sigma^2$. Find the Cramer-Rao lower bound for the variance of an unbiased estimator of $\mu$.

克拉默-劳（Cramer-Rao）下界是一个用于评估无偏估计量方差的下限的工具。对于正态分布，均值 $\mu$ 的无偏估计量的方差的克拉默-劳下界是 $\frac{\sigma^2}{n}$。所以，对于你的问题，答案是 $\frac{\sigma^2}{n}$。

这是因为克拉默-劳下界是由以下公式给出的：

$
Var(\hat{\tau(\theta)}) \geq \frac{[\tau'(\theta)]}{I_n(\theta)}
$

其中，$\hat{\tau(\theta)}$ 是参数 $\tau(\theta)$ 的无偏估计量，$I(\theta)$ 是费舍尔信息。已知 $\tau(\theta) = \mu$。


pdf:

$$
f({x_1}|\mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{1}{2\sigma^2} (x_1 - \mu)^2}
$$

ln:

$$
ln f({x_1}|\mu, \sigma^2) = - \frac{1}{2\sigma^2} (x_1 - \mu)^2 - ln(\sqrt{2\pi\sigma^2})
$$

derivative:

$$
\frac{\partial}{\partial \mu} ln f({x_1}|\mu, \sigma^2) = \frac{1}{\sigma^2} (x_1 - \mu)
$$

代入I的公式：

$$ I_1(\mu) = E[(\frac{\partial}{\partial \mu} ln f({x_1}|\mu, \sigma^2))^2] \\ = \frac{E[(x-\mu)^2]}{\sigma^4} \\= \frac{Var(x)}{\sigma^4} = \frac{\sigma^2}{\sigma^4} = \frac{1}{\sigma^2}
$$

费舍尔信息 $I_n(\mu) = n\dot{I_1(\mu)} = \frac{n}{\sigma^2}$

$
Var(\hat{\mu}) \geq \frac{1}{I(\mu)} = \frac{\sigma^2}{n}
$

所以，对于正态分布，均值 $\mu$ 的无偏估计量的方差的克拉默-劳下界是 $\frac{\sigma^2}{n}$。

## 2

Consider the same random sample as in the previous question. Assume $\mu$ is known and find the Cramer-Rao lower bound for the variance of an unbiased estimator of $\sigma^2$.

对于正态分布 $N(\mu, \sigma^2)$，我们知道其概率密度函数（PDF）为：

$$
f(x;\mu,\sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$

我们可以计算对数似然函数的导数：

$$
\frac{\partial}{\partial \sigma^2}\log f(X;\mu,\sigma^2) = -\frac{1}{2\sigma^2} + \frac{(X - \mu)^2}{2\sigma^4}
$$

然后，我们可以计算这个导数的平方的期望值，得到费舍尔信息：

$$
E\left[\left(\frac{\partial}{\partial \sigma^2}\log f(X;\mu,\sigma^2)\right)^2\right] = E\left[\left(-\frac{1}{2\sigma^2} + \frac{(X - \mu)^2}{2\sigma^4}\right)^2\right]
$$

我们可以将上式展开并简化为：

$$
E\left[\frac{1}{4\sigma^4} - \frac{(X - \mu)^2}{2\sigma^6} + \frac{(X - \mu)^4}{4\sigma^8}\right]
$$

我们知道 $$E[X] = \mu$，$E[(X - \mu)^2] = \sigma^2$，并且 $E[(X - \mu)^4] = 3\sigma^4$。所以，我们可以将上式简化为：

$$
\frac{1}{4\sigma^4} - \frac{\sigma^2}{2\sigma^6} + \frac{3\sigma^4}{4\sigma^8} = \frac{1}{2\sigma^4}
$$

这就是导数的平方的期望值的计算步骤。

### 我们可以用计算二阶导数的方法来计算费舍尔信息：

$$
I_1(\sigma^2) = E[\frac{\partial ^{2}}{\partial \sigma^4}(\log f(X;\mu,\sigma^2))] \\ = E[\frac{\partial}{\partial t}(-\frac{1}{2t} + \frac{(X - \mu)^2}{2t^2})|_{t=\sigma^2}] \\ = E[\frac{1}{2\sigma^4} - \frac{(X - \mu)^2}{\sigma^6}] \\ = \frac{1}{2\sigma^4}
$$

$$
I_1(\sigma^2) = E\left[\left(\frac{\partial}{\partial \sigma^2}\log f(X;\mu,\sigma^2)\right)^2\right] = \frac{1}{2\sigma^4}
$$

如果我们有一个大小为 $n$ 的样本，那么总的费舍尔信息就是单个观测的费舍尔信息的 $n$ 倍，即：

$$
I_n(\sigma^2) = \frac{n}{2\sigma^4}
$$

因此，对于正态分布，方差 $\sigma^2$ 的无偏估计量的方差的克拉默-劳下界是 $\frac{2\sigma^4}{n}$。

## 3

Suppose $X_1, X_2, \ldots, X_n$ is a random sample from a Poisson distribution with parameter $\lambda$. Find the Cramer-Rao lower bound for the variance of an unbiased estimator of $P(X_i = 0)$.

对于泊松分布，我们知道 $P(X_i = 0) = e^{-\lambda}$。所以，我们实际上是在寻找 $e^{-\lambda}$ 的无偏估计量的方差的克拉默-劳（Cramer-Rao）下界。

首先，我们知道泊松分布的参数 $\lambda$ 的最大似然估计是样本均值 $\bar{X}$，并且其方差的克拉默-劳下界是 $\frac{\lambda}{n}$。

然后，由于 $e^{-\lambda}$ 是 $\lambda$ 的函数，我们可以使用克拉默-劳下界的不等式，得到：

$$
Var(e^{-\hat{\lambda}}) \geq \left(\frac{d}{d\lambda} e^{-\lambda}\right)^2 \frac{\lambda}{n} = e^{-2\lambda} \frac{\lambda}{n}
$$

其中，$\hat{\lambda} = \bar{X}$ 是 $\lambda$ 的最大似然估计。

所以，对于这个问题，所有无偏估计量 $e^{-\hat{\lambda}}$ 的方差的克拉默-劳下界是 $$e^{-2\lambda} \frac{\lambda}{n}$$。

对于泊松分布，我们有 $\theta = \lambda$，并且费舍尔信息 $I(\lambda) = n / \lambda$。