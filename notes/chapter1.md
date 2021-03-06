# Chapter 1-绪论

## 机器学习和其任务

机器学习研究的主要内容：学习算法。从数据中产生模型（model）的算法。

Mitchell 给出一个更形式化的定义：假设用 P 来评估计算机在任务 T 上的性能，若一个程序利用经验 E 在 T 中任务上取得了性能上的改善，则我们说关于 P 和 T，改程序对 E 进行了学习。

分类、回归和聚类是机器学习的三大任务。分类和回归都是预测任务，区别在于预测值是离散还是连续；聚类将训练集中的数据分成若干组（簇），以帮助发现一些数据内在的规律。

泛化能力（generalization）：学得模型适用于新样本的能力。能够反映出样本空间的特性的训练集越有可能经过学习得到具有强泛化能力的模型。

归纳和演绎是科学推理的两大基本手段。前者从特殊到一般，从具体的事实归结出规律；后者则是一般到特殊，由基础原理推导出具体情况。“从样例中学习”的机器学习是一种归纳学习。

## 归纳偏好

学习过程可以看做是在所有假设组成的空间中进行搜索的过程，而可能存在多个假设与训练集一致，即存在一个“假设集合”。

机器学习算法在学习过程中对某种类型假设的偏好，成为“归纳偏好”。

归纳偏好可以看做是算法选择的“价值观”，**奥卡姆剃须刀**是一种一般性原则来引导算法确立正确的价值观：

> 若有多个假设与观察一致，则选择最简单的那个、

在具体问题上，算法的归纳偏好需要与问题相匹配，才能得到好的性能。

没有免费的午餐（NFL）定理：

> 任意两个算法的期望性能相同

其有一个重要前提：所有问题出现的机会相同，或者问题同等重要，即目标函数 $f(x)$ 服从均匀分布，但这不符合实际。NFL 最重要寓意：**脱离具体问题，空泛地谈论什么学习算法更好，没有任何意义**。

简化证明如下：

假设样本空间 $\chi$ 和假设空间 H 都是离散的，令 $P(h|X, L_a)$ 表示算法 $L_a$ 基于训练数据 $X$ 产生假设 $h$ 的概率，$f(x)$ 为目标函数，$\ell(x, y)$ 为性能度量函数，则 $L_a$ 的训练集外误差为：

$$ E_{ote}(L_a|X,f) = \sum_ h \sum_{x \in \chi - X} P(\mathbf{x}) \ell(h(x), f(x))P(h|X, L_a)$$ 

考虑二分类问题，对所有可能的 $f$ 按均匀分布对误差求和：

$$\sum_f E_{ote}(L_a|X,f) = \sum_f \sum_ h \sum_{x \in \chi - X} P(\mathbf{x}) \ell(h(x), f(x))P(h|X, L_a) \\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \\ \ \ \ \ \ = \sum_{x \in \chi - X} P(\mathbf{x})  \sum_ h P(h|X, L_a)\sum_f\ell(h(x), f(x))$$ 

对于任意一个确定的函数 $h(x)$，性能度量函数为一常数 $C$，然后根据条件概率 $\sum_ h P(h|X, L_a)$ 求和为 1，上式等于：

$$\sum_f E_{ote}(L_a|X,f) = C \sum_{x \in \chi - X} P(\mathbf{x})   $$

即，总误差与学习算法无关。















