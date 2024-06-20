# Method of Moments Estimation Quiz

一阶矩就是期望值
二阶(非中心)矩就是对变量的平方求期望

中心矩则类似于方差，先要得出样本的期望即均值，然后计算出随机变量到样本均值的一种距离，与方差不同的是，方差是二阶中心矩，而中心矩是任意阶的。
二阶中心距，也叫作方差，是指随机变量与其均值之差的平方的期望值，即$E[(X-E(X))^2]$。它是衡量随机变量的离散程度的一个重要指标。
三阶中心距，是指随机变量与其均值之差的立方的期望值，即$E[(X-E(X))^3]$。它是衡量随机变量分布的不对称性的一个重要指标，告诉我们分布的尾部是向左还是向右偏。

A1,一阶矩就是 E(X),即样本均值。具体说来就是$A_1=({\sigma}X_i/n)$ ----（1）
A2,二阶矩就是 E(X^2)即样本平方均值 ,具体说来就是 $A_2=({\sigma}X_i^2/n)$-----(2)
Ak,K阶矩就是 E(X^k)即样本K次方的均值,具体说来就是 $A_k=({\sigma}X_i^k/n)$，-----(3)

矩估计法大概步骤如下：
1 根据分布律或者分布函数，概率函数，计算EX或者EX2,其中含有未知参数a。
2 令 样本的一阶矩A1等于EX（二阶矩A2等于EX^2)。
3 由2得到 a的表达式子，此式子中含有A1(A2,...),而A1,A2表达式如上(1),(2)，（3）所示.
该含有 A1,A2,..Ak的表达式称为估计量，如果把样本具体值带入，即可得a的估计值。

## 1 

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the Bernoulli distribution with parameter 𝑝. Let 
$\hat{p}$ be the method of moments estimator for 𝑝. 

Which of the following is true. (Check all that apply.)

- $\hat{p}$ 是 $p$ 的无偏估计器。这是因为 $\hat{p}$ 是样本均值，对于伯努利分布，样本均值是参数 $p$ 的无偏估计器。 
- $\hat{p}$ 是样本中等于1的值的比例。这是因为在伯努利试验中，"成功"（即 $X_i = 1$）的概率就是 $p$，所以样本中等于1的值的比例是 $p$ 的一个自然估计。 
- $\hat{p}$ 是样本均值。这是因为 $\hat{p}$ 是所有 $X_i$ 的平均值，其中 $X_i$ 是从伯努利分布中抽取的样本。 
- 但是，$Var[\hat{p}] = 1$ 是不正确的。对于伯努利分布，$Var[\hat{p}]$ 实际上是 $\frac{p(1-p)}{n}$，其中 $n$ 是样本大小。因此，除非 $p(1-p) = n$，否则 $Var[\hat{p}]$ 不可能等于1。在大多数情况下，这是不可能的，因为 $p$ 是概率（必须在0和1之间），而 $n$ 是样本大小（通常是一个大于1的整数）。因此，这个说法是错误的。


## 2 

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the geometric distribution with parameter 𝑝 , that takes on the values 0,1,2,….
What is the method of moments estimator of 𝑝. 

当然可以。对于几何分布，我们知道其期望值 $E[X] = \frac{1-p}{p}$。这是因为几何分布的定义是：直到第一次成功需要的试验次数，其中每次试验成功的概率为 $p$。

矩估计法的基本思想是将参数的理论矩（即基于概率分布的矩）设为对应的样本矩（即基于样本数据的矩）。对于几何分布，我们只需要考虑一阶矩，即期望值。

所以，我们将样本均值 $\bar{X}$ 设为理论期望 $E[X] = \frac{1-p}{p}$，解出 $p$，得到：

$$\bar{X} = \frac{1-p}{p}$$
$$p\bar{X} = 1 - p$$
$$p(\bar{X} + 1) = 1$$
$$p = \frac{1}{\bar{X} + 1}$$

这就是参数 $p$ 的矩估计方法。注意，这里的几何分布是以 $0$ 为起点的。因此，我们在计算样本均值时要加上 $1$。这就是 $\hat{p} = \frac{1}{\bar{X} + 1}$ 的推导过程。

## 3

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the Beta distribution with parameters 𝑎 and b.

what is the method of moments estimators for 𝑎 and 𝑏?

对于Beta分布，我们知道其一阶原点矩（期望值）和二阶中心矩（方差）分别为 $E[X] = \frac{a}{a+b}$ 和 $Var[X] = \frac{ab}{(a+b)^2(a+b+1)}$。

矩估计法的基本思想是将参数的理论矩设为对应的样本矩。所以，我们将样本均值 $\bar{X}$ 设为理论期望 $E[X]$，并将样本方差 $s^2$ 设为理论方差 $Var[X]$，解出 $a$ 和 $b$。

设 $\bar{X} = \frac{a}{a+b}$ 和 $s^2 = \frac{ab}{(a+b)^2(a+b+1)}$，我们可以得到以下的矩估计方法：

$a = \bar{X} \left( \frac{\bar{X}(1 - \bar{X})}{s^2} - 1 \right)$
$b = (1 - \bar{X}) \left( \frac{\bar{X}(1 - \bar{X})}{s^2} - 1 \right)$

其中，$\bar{X}$ 是样本均值，$s^2$ 是样本方差。这就是参数 $a$ 和 $b$ 的矩估计方法。

## 4

Let 𝑋1,𝑋2,…,𝑋𝑛 be a random sample from the continuous Pareto distribution as given in the table of distributions for this course. What is the method of moments estimator of the parameter 𝛾?

$$E[X] = \frac{1}{\gamma - 1}$$
$$\bar{X} = \frac{1}{\gamma - 1}$$
$$\gamma - 1 = \frac{1}{\bar{X}}$$
$$\gamma = \frac{1}{\bar{X}} + 1$$

## 5

Method of moments estimators are guaranteed to be unbiased estimators.

False

矩估计法并不能保证估计量是无偏的。虽然在某些情况下，矩估计法可以得到无偏估计量，但这并不总是成立。所以，"矩估计法的估计量一定是无偏的"这个说法是错误的。
让我们考虑正态分布的方差 $\sigma^2$ 的矩估计量。

假设我们有一个来自正态分布 $N(\mu, \sigma^2)$ 的随机样本 $X_1, X_2, ..., X_n$。样本方差定义为：

$$s^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})^2$$

其中，$\bar{X}$ 是样本均值。这是 $\sigma^2$ 的矩估计量。

然而，这个估计量是有偏的。实际上，它的期望值是 $E[s^2] = \frac{n-1}{n} \sigma^2$，这不等于 $\sigma^2$，除非 $n$ 趋向于无穷大。因此，$s^2$ 是 $\sigma^2$ 的有偏估计量。

为了得到无偏估计量，我们通常使用修正样本方差：

$$s^2_{unbiased} = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})^2$$

这个估计量的期望值是 $E[s^2_{unbiased}] = \sigma^2$，所以它是无偏的。但是，如果我们仅仅使用矩估计法，我们会得到有偏的估计量 $s^2$。这就是一个矩估计量不是无偏的例子。希望这个解释对你有所帮助！

