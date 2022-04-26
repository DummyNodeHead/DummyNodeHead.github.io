# Explaining And Harnessing Adversarial Examples



## 攻击方式

$$
\eta=\epsilon sign(\nabla_xJ(\theta,x,y))
$$

其中，$\eta$ 是添加的扰动，$\epsilon$ 是超参数。首先通过计算损失函数 $J$ 对 $x$ 的梯度**（不是对 $\theta$ ）**，将其带入符号函数，最后乘上 $\epsilon$ 得到扰动。对抗样本即为：
$$
\tilde{x}=x+\eta
$$
个人认为此攻击方式与梯度下降类似，只不过一个是求权重的偏导，一个是求x的。



## 为何攻击有效

考虑权重向量 $\omega$ 和对抗样本 $\tilde{x}$ 的乘积：
$$
\omega^T \tilde{x}=\omega^Tx+\omega^T\eta
$$
可以得知，扰动使得激活函数的激活程度增长了$\omega^T\eta$。可以通过 $\eta$ 的无穷范数来最大化这个增长。如果 $\omega$ 有 $n$ 维，且它的每个元素的平均量级为 $m$，那么整个激活程度就会增长 $\epsilon mn$ 。



## 对抗样本的线性解释

文章认为产生对抗样本的原因是因为模型的linear性质。
