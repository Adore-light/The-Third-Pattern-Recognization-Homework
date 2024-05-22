# The-Third-Pattern-Recognization-Homework
这是模式识别与机器学习的第三次作业
由三个部分组成：
1.公式推导
我之前听过吴恩达老师和李宏毅老师关于EM算法的课程，收获了琴生不等式导出ELBO和根据条件概率公式导出ELBO+KL散度两个思路，在这里分别使用这两个思路推出EM算法将极大似然MLE推广为极大化ELBO的过程。

对于本次作业题目，我们建立了高斯混合模型，并根据先前推出的ELBO形式进一步推导出了本题的 $Q\left( \theta ,\theta ^{\left( t \right)} \right)$，得到了本题五个参数（推导过程写了六个，不过两个高斯模型的权重系数满足 $\pi_1 + \pi_2 = 1$，所以实际只有五个参数）。
2.实验报告部分：随机产生了1000个数据点，应用了混合高斯模型

3.代码部分

其中在原理推导部分
为了便于推导过程的理解，在这里我对我使用的一些函数写法进行说明：

$$
X:\text{为连续的显变量,可以取}x_1,x_2,x_3...,x_N
$$

$$
Z\text{：为连续的隐变量，可以取}z_1,z_2,z_3...,z_N
$$

$$
Y\text{：为完整变量，可以取}\left( x_1,z_1 \right), \ldots, \left( x_N,z_N \right)
$$


$$
Z\text{在本题中可以取的值为}C_1,C_2\text{表示男性和女性}
$$

$$
\pi _1,\pi _2:\text{分别取}Z\text{取}C_1,C_2\text{的概率}
$$

$$
k:\text{用于遍历数据点1~}N\text{的角标}
$$

$$
m:\text{用于遍历隐变量}Z_k\text{取值的角标，每一个}Z_k\text{有两个取值分别为}C_1,C_2
$$

$$
p\left( x,z|\theta \right) :\text{在参数域}\theta \text{下完整变量}Y\text{的分布函数}
$$

$$
p\left( x|\theta \right) :\text{在参数域}\theta \text{下显变量的分布函数}
$$

$$
p\left( z|x,\theta \right) :\text{给定}x\text{后，在参数域}\theta \text{下}z\text{的后验概率}
$$

$$
q\left( z \right) :z\text{的实际分布函数}
$$

$$
p\left( z|x,\theta ^{\left( t \right)} \right) \text{：给定}x\text{后，在得到第}t\text{步的}\theta ^{\left( t \right)}\text{下}z\text{的后验概率}
$$

$$
N\left( x|u,\sigma \right) :pdf\text{函数}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{\left( x-u \right) ^2}{\sigma ^2}}
$$

$$
p\left( Z_k \right) :Z_k\text{取}C_1\text{时}p\left( Z_k \right) =\pi _1,Z_k\text{取}C_2\text{时}p\left( Z_k \right) =\pi _2
$$

$$
\mu _{Z_k}:Z_k\text{取}C_1\text{时}\mu _{Z_k}=\mu _1,Z_k\text{取}C_2\text{时}\mu _{Z_k}=\mu _2
$$

$$
\sigma _{Z_k}:Z_k\text{取}C_1\text{时}\sigma _{Z_k}=\sigma _1,Z_k\text{取}C_2\text{时}\sigma _{Z_k}=\sigma _2
$$

补充公式：

$$
P\left( A,B \right) =P\left( A \right) P\left( B|A \right) 
$$

$$
P\left( A \right) =\sum_{i=1}^n{P\left( A_i \right) P\left( B|A_i \right)}
$$

$$
P\left( A_k\mid B \right) =\frac{P\left( A_k \right) P\left( B\mid A_k \right)}{P\left( B \right)}=\frac{P\left( A_k \right) P\left( B\mid A_k \right)}{\sum_{i=1}^n{P}\left( A_i \right) P\left( B\mid A_i \right)}
$$

琴生不等式：

$$
\frac{\sum_{i=1}^n{f}\left( x_i \right)}{n}\geq f\left( \frac{\sum_{i=1}^n{x}_i}{n} \right) 
$$


