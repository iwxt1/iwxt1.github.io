---
title: 'Information theory basics'
date: 2023-10-18
permalink: /posts/2023/10/information-theory
excerpt_separator: <!--more-->
toc: true
tags:
  - information-theory
---

信息论基础。
<!--more-->
# 自信息（Self-Information）





度量概率分布带来的信息：



$$
\begin{equation*}
I(x) = -\log P(x)
\end{equation*}
$$



$\log$是以$e$为底的自然对数，单位奈特（nats），比特或香农（2为底）。



# 香农熵（Shannon Entropy）





度量概率分布系统的混乱度，由概率赋权，系统信息量的期望：




$$
\begin{equation*}
H(x) = \mathbb{E}_{x\sim P} \left[ I(x) \right] = -\mathbb{E}_{x\sim P}\left[\log P(x) \right]
\end{equation*}
$$



熵给出了对概率分布编码所需的比特数（或奈特数）在**平均意义**上的下界。系统越接近确定性的分布，熵越低；系统越接近均匀分布，熵越高。



## 相对熵（Killback-Leibler Divergence）





从混乱度角度，度量**两个**概率分布系统的相似度：



$$
\begin{align*}
D_{KL}(P||Q) &= \mathbb{E}_{x\sim P}\left[ \log \frac{P(x)}{Q(x)} \right]\\
&= \sum_{i=1}^m p_i(-\log q_i) - \sum_{i=1}^m p_i(-\log p_i)\\
&\ge 0
\end{align*}
$$




Q对于P的散度，吉布斯不等式得到$\ge$，观察展开前一项为交叉熵，后一项为系统P的香农熵，得到P和Q的交叉熵不小于P的香农熵，香农熵不小于0，所以交叉熵也不小于0，而KL散度越小，P和Q越接近，所以交叉熵越小，两系统越接近。因此，交叉熵可以用于损失函数。



## 交叉熵（Cross Entropy）





交叉熵越小，损失越小，两个模型越接近：



$$
\begin{equation*}
H(P,Q) = \sum_{i=1}^m p_i(-\log q_i)
\end{equation*}
$$




## 条件熵（Conditional Entropy）





在已知 X 的取值的情况下，Y 的不确定性。




$$
\begin{align*}
H(Y\mid X) &= \sum_x p(x)H(Y\mid X = x)\\
&= -\sum_x p(x)\sum_y p(y\mid x)\log p(y\mid x)\\
&= -\sum_{x,y}p(x,y)\log(y\mid x)
\end{align*}
$$




条件熵可以用来衡量随机变量之间的依赖关系。当条件熵较高时，表示两个变量之间的关联性较弱；当条件熵较低时，表示两个变量之间的关联性较强。





## 互信息（Mutual Information）





表示通过观察 X 来减少 Y 的不确定性，或通过观察 Y 来减少 X 的不确定性的量。$I(X;Y)$代表$X$和$Y$两个变量的相关性，且$I(X;Y) = I(Y;X)\;$。




$$
\begin{equation*}
I(X;Y) = H(X) - H(X\mid Y)
\end{equation*}
$$




若$X$，$Y$互相独立，则$I(X;Y) = 0\;$。