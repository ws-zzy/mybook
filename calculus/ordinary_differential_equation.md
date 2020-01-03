在数学分析中，**常微分方程**（英语：ordinary differential equation，简称ODE）是未知函数只含有一个自变量的微分方程。

很多科学问题都可以表示为常微分方程，例如根据牛顿第二运动定律，物体在力的作用下的位移$s$和时间$t$的关系就可以表示为如下常微分方程：
$$
m\frac{d^2s}{dt^2}=f(s)
$$

其中 $m$是物体的质量，$f(s)$是物体所受的力，是位移的函数。所要求解的未知函数是位移 $s$，它只以时间 $t$ 为自变量。

## 可分离方程

#### 一阶，变量 $x$ 和 $y$ 均可分离（一般情况, 下面有特殊情况）

$$
P_{1}(x)Q_{1}(y)+P_{2}(x)Q_{2}(y) {\frac {dy}{dx}}=0 \\
P_{1}(x)Q_{1}(y) dx+P_{2}(x)Q_{2}(y) dy=0
$$

##### 解法

  分离变量（除以$ P_{2}Q_{1}$）。

##### 通解

$$
\int ^{x}{\frac {P_{1}(\lambda )}{P_{2}(\lambda )}} d\lambda +\int ^{y}{\frac {Q_{2}(\lambda )}{Q_{1}(\lambda )}} d\lambda =C
$$

#### 一阶，可化为变量可分离型

$$
\frac {dy}{dx}=F(ax+by+c) 
$$

其中$a$，$b$不全为零

##### 解法

令
$$
u=ax+by+c
$$
，则
$$
{\frac{du}{dx}} = a+b{\frac{dy}{dx}}
$$

##### 通解

$$
x=\int ^{ax+by+c}{\frac {d\lambda }{a+bf(\lambda )}}+C
$$

## 一般一阶微分方程
#### 一阶，齐次

$$
{\frac {dy}{dx}}=F({\frac {y}{x}})
$$

##### 解法

令 $y=ux$，然后通过分离变量 $u$ 和 $x$ 求解。

##### 通解

$$
\ln(Cx)=\int ^{\frac {y}{x}}{\frac{d\lambda }{F(\lambda )-\lambda }}
$$

#### 一阶，可分离变量

$$
yM(xy)+xN(xy) {\frac {dy}{dx}}=0 \\

yM(xy) dx+xN(xy) dy=0
$$

##### 解法

分离变量（除以 $xy$）。

##### 通解

$$
\ln(Cx)=\int ^{xy}{\frac {N(\lambda ) d\lambda }{\lambda [N(\lambda )-M(\lambda )]}}
$$

如果$N=M$, 解为$xy=C$。

#### 恰当微分, 一阶

$$
M(x,y){\frac {dy}{dx}}+N(x,y)=0 \\

M(x,y)\,dy+N(x,y) dx=0
$$

其中 ${\frac {\partial M}{\partial x}} = {\frac {\partial N}{\partial y}}$

##### 解法

整个积分。

##### 通解

$$
F(x,y)=\int ^{y}M(x,\lambda ) d\lambda +\int ^{x}N(\lambda ,y) d\lambda +Y(y)+X(x)=C
$$


其中 $Y(y)$ 和 $X(x)$ 是积分出来的函数而不是常数，将它们列在这里以使最终函数$F(x,y)$满足初始条件。

#### 反常微分, 一阶

$$
M(x,y){\frac {dy}{dx}}+N(x,y)=0 \\

M(x,y) dy+N(x,y) dx=0
$$

其中${\frac {\partial M}{\partial x}}\neq {\frac {\partial N}{\partial y}}\,\!$

##### 解法

积分变量 $μ(x,y)$满足
$$
{\frac {\partial (\mu M)}{\partial x}}={\frac {\partial (\mu N)}{\partial y}}
$$

##### 通解

如果可以得到 $μ(x,y)$:
$$
F(x,y)=\int ^{y}\mu (x,\lambda )M(x,\lambda ) d\lambda +\int ^{x}\mu (\lambda ,y)N(\lambda ,y) d\lambda +Y(y)+X(x)=C
$$

## 一般二阶微分方程
#### 二阶, 自治

$$
{\frac {\mathrm {d} ^{2}y}{\mathrm {d} x^{2}}}=F(y)
$$

##### 解法

原方程乘以 ${\frac {2\mathrm {d} y}{\mathrm {d} x}}$ ，代换
$$
2{\frac {\mathrm {d} y}{\mathrm {d} x}}{\frac {\mathrm {d} ^{2}y}{\mathrm {d} x^{2}}}={\frac {\mathrm {d}}{\mathrm {d} x}} ({\frac {\mathrm {d} y}{\mathrm {d} x}})^{2}
$$


，然后两次积分。

##### 通解

$$
x=\pm \int ^{y}{\frac {\mathrm {d} \lambda }{\sqrt {2\int ^{\lambda }F(\epsilon )\,\mathrm {d} \epsilon +C_{1}}}}+C_{2}
$$

#### 二阶可降阶，${\frac{d^2y}{dx^2}=f(x, {\frac{dy}{dx}})}$

##### 解法

令${\frac{dy}{dx} = p(x)}$，$\frac{d^2y}{dx^2}={\frac{dp}{dx}}$，则原方程变为
$$
{\frac{dp}{dx}} = f(x, p)
$$


#### 二阶可降阶，${\frac{d^2y}{dx^2}=f(y, {\frac{dy}{dx}})}$

##### 解法

令${\frac{dy}{dx} = p(x)}$，$\frac{d^2y}{dx^2}={\frac{dp}{dx}}={\frac{dp}{dy}} \cdot {\frac{dy}{dx}} = {\frac{dp}{dy}} \cdot p$，则原方程变为
$$
{\frac{dp}{dy}} = f(y, p)
$$

## 线性方程 (最高到$n$阶)

####  一阶线性，非齐次的函数系数

$$
{\frac {dy}{dx}}+P(x)y=Q(x)
$$

##### 解法

积分因子: $e^{\int ^{x}P(\lambda )\,d\lambda }$。

##### 通解

$$
y=e^{-\int ^{x}P(\lambda ) d\lambda }[\int ^{x}e^{\int ^{\lambda }P(\epsilon ) d\epsilon }Q(\lambda ) {d\lambda }+C]
$$

#### 二阶线性，非齐次的常系数

$$
{\frac {d^{2}y}{dx^{2}}}+b{\frac {dy}{dx}}+cy=r(x)
$$

##### 解法

余函数 $y_{c}$: 设 $y_{c}=\mathrm {e} ^{\alpha x}$，代换并解出 $\alpha$  中的多项式，求出线性无关函数 $e^{\alpha _{j}x}$。
特解 $y_{p}$：一般运用常数变易法，虽然对于非常容易的 $r(x)$ 可以直观判断。

##### 通解

$$
y=y_{c}+y_{p}
$$


如果 $b^{2}>4c$, 则:
$$
y_{c}=C_{1}e^{(-b+{\sqrt {b^{2}-4c}}){\frac {x}{2}}}+C_{2}e^{(b+{\sqrt {b^{2}-4c}}){\frac {x}{2}}}
$$
如果 $b^{2}=4c$, 则:
$$
 y_{c}=(C_{1}x+C_{2})e^{-{\frac {bx}{2}}}
$$
如果 $b^{2}<4c$, 则:

$$
y_{c}=e^{-{\frac {bx}{2}}} [C_{1}\sin {({\sqrt {|b^{2}-4c|}}{\frac {x}{2}})}+C_{2}\cos {({\sqrt {|b^{2}-4c|}}{\frac {x}{2}})}]
$$

#### $n$ 阶线性，非齐次常系数

$$
\sum _{j=0}^{n}b_{j}{\frac {d^{j}y}{dx^{j}}}=r(x)
$$

##### 解法

余函数 $y_{c}$：设 $y_{c}=\mathrm {e} ^{\alpha x}$，代换并解出 $\alpha$ 中的多项式，求出线性无关函数 $e^{\alpha _{j}x}$。
特解 $y_{p}$：一般运用常数变易法，虽然对于非常容易的 $r(x)$ 可以直观判断。

##### 通解

$$
y=y_{c}+y_{p}
$$


由于 $\alpha _{j}$ 为 n 阶多项式的解：$\prod _{j=1}^{n} (\alpha -\alpha _{j})=0$，于是：

对于各不相同的 $\alpha _{j}$，
$$
y_{c}=\sum _{j=1}^{n}C_{j}e^{\alpha _{j}x}
$$
每个根 $\alpha _{j}$ 重复  $k_{j}$ 次，

$$
y_{c}=\sum _{j=1}^{n} (\sum _{\ell =1}^{k_{j}}C_{\ell }x^{\ell -1})e^{\alpha _{j}x}
$$
对于一些复数值的 $\alpha_{j}$，令 $\alpha_{j} = \chi_{j} + i\gamma_{j}$，使用欧拉公式，前面结果中的一些项就可以写成

$$
e^{\alpha _{j}x}=e^{\chi _{j}x}\cos(\gamma _{j}x+\phi _{j})
$$

的形式，其中 $\phi _{j}$ 为任意常量（相移）。

#### 伯努利方程

$$
{\frac {dy}{dx}}+P(x)y=Q(x){\frac {d^{n}y}{dx^{n}}}, n \neq 1, 2
$$

##### 解法

变形为$y^{-n} \cdot {\frac{dy}{dx}} + P(x)y^{1-n}=Q(x)$

令$z = y^{1-n}$，得${\frac{dz}{dx}} = (1-n)y^{-n}{\frac{dy}{dx}}$， 则${\frac{1}{1-n}}{\frac{dz}{dx}}+P(x)z=Q(x)$

##### 通解

按照一阶线性微分方程求解即可。