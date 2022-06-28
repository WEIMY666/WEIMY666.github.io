### Adaboost算法（分类）

![img](https://pic1.zhimg.com/80/v2-6dfc944cd6c241d5fb47405173d957fc_720w.jpg)

输入：训练数据集
$$
T = \left \{ (x_1,y_1),(x_2,y_2),(x_N,y_N)\right \}
$$
其中
$$
x_{i} \in \chi \subseteq R^{n},y_i \in \gamma=\left \{+1,-1 \right\},i=1,2,...N
$$
弱学习算法输出为分类器G(x)。

#### 1. 初始化训练数据的权重（等权重）

$$
D_1 = (w_{11},w_{12}...,w_{1N}),w_{1i}=\frac{1}{N},i=1,2,...N
$$

#### 2.使用具有权重分布$D_M$的训练数据集学习，得到基本分类器

$$
G_{m}(x):\chi \to \left \{-1,+1\right\}
$$

计算$G_m(x)$在训练数据集上的分类误差率
$$
e_m=\sum_{i=1}^{N}P(G_m(x_i))\ne y_i)
	
	=\sum_{i=1}^{N}w_{mi}I(G_m(x_i))\ne y_i)
$$
计算$G_m(x)$的系数
$$
\alpha_m=\frac{1}{2}log\frac{1-e_m}{e_m}
$$
更新训练数据集的权值分布
$$
D_{m+1}=(w_{m+1,1},...,w_{m+1,i}...,w_{m+1,N})
$$

$$
w_{m+1,i}=\frac{w_{mi}}{Z_{m}}exp(-\alpha_my_iG_m(x_i)),
$$

$$
=\left\{\begin{matrix} 
  \frac{w_{mi}}{Z_m}exp(-\alpha_m),G_m(x_i)=y_i \\  
  \frac{w_{mi}}{Z_m}exp(\alpha_m),G_m(x_i)\ne y_i
\end{matrix}\right.
$$

其中，$Z_m$是规范化因子
$$
Z_m=\sum_{i=1}^{N}w_{mi}exp(-\alpha_m y_i,G_m(x_i))
$$
构建基本分类器的线性组合
$$
f(x)=\sum_{m=1}^{N}\alpha_mG_m(x)
$$
得到了最终的分类器！
$$
G(x)=sign(f(x))=sign(\sum_{m=1}^{M}\alpha_mG_m(x))
$$

##### 注1：以上为二分类的建模，对于多元变量差别只是在弱分类器的系数上：

$$
\alpha_m=\frac{1}{2}log\frac{1-e_m}{e_m}+log(R-1)
$$

R为分类别数。如果是二元分类，则和二元分类算法中的系数一致。

##### 注2: $\alpha$ 随着$e_{m}$的减少而增大，所以误分类误差率越小的基本分类器在最终分类器的作用越大，符合预期。

##### 注3：这里的$\alpha_m$表示了基本分类器$G_M$的重要性，所以和不为1。 



### AdaBoost算法（回归）

#### 1. 初始化训练数据的权重（等权重）

$$
D_1 = (w_{11},w_{12}...,w_{1N}),w_{1i}=\frac{1}{N},i=1,2,...N
$$

#### 2.使用具有权重分布$D_M$的训练数据集学习，得到基本分类器$G_m(x)$

计算训练集上的最大误差
$$
E_M = max\left | y_i-G_m(x_i) \right |
$$
计算每个样本的相对误差：
$$
\left\{\begin{matrix} 
  如果是线性的误差，则e_{mi}=\frac{\left | y_i-G_m(x_i) \right |}{E_m}\\  
  如果是平方误差，则e_{mi}=\frac{(y_i-G_m(x_i))^2}{E_m^2}\\
  如果是指数误差，则e_{mi}=1-exp(\frac{-y_i+G_m(x_i)}{E_m})
\end{matrix}\right.
$$
计算回归误差率：
$$
e_m=\sum_{i=1}^{N}w_{mi}e_{mi}
$$
并计算弱学习器的系数：
$$
\alpha_m=\frac{e_m}{1-e_m}
$$
最终更新样本集的权重分布为:
$$
w_{m+1,i}=\frac{w_{mi}}{Z_m}\alpha_{m}^{1-e_{mi}}
$$
其中
$$
Z_m=\sum_{i=1}^{N}w_{mi}\alpha_{m}^{1-e_{mi}}
$$

#### 3.构建基本分类器的线性组合

$$
f(x)=\sum_{m=1}^{M}(ln\frac{1}{\alpha_m})g(x)
$$

其中，$g(x)$是所有$\alpha_mG_m(x),m=1,2...M$的中位数。





**从另一个角度，AdaBoost还有一种解释，即可认为AdaBoost算法是模型为加法模型、损失函数为指数函数、学习算法为前向分布算法时的二类分类学习方法。**[](https://zhuanlan.zhihu.com/p/39972832)

### 

### Adaboost的优缺点

##### 优点：

##### Adaboost提供一种框架，在框架内可以使用各种方法构建子分类器。可以使用简单的弱分类器，不用对特征进行筛选，也**不存在过拟合的现象**。

**Adaboost可以根据弱分类器的反馈，自适应地调整假定的错误率，执行的效率高。**

**缺点：**

**在Adaboost训练过程中，Adaboost会使得难于分类样本的权值呈指数增长，训练将会过于偏向这类困难的样本，导致Adaboost算法易受噪声干扰。此外，Adaboost依赖于弱分类器，而弱分类器的训练时间往往很长。**



























