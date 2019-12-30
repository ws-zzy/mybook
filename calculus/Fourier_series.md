在数学中，**傅里叶级数**（**fourier series**，[/ˈfʊrieɪ, -iər/]）是把类似波的函数表示成简单正弦波的方式。更正式地说，它能将任何周期函数或周期信号分解成一个（可能由无穷个元素组成的）简单振荡函数的集合，即正弦函数和余弦函数（或者，等价地使用[复指数](https://zh.wikipedia.org/wiki/复指数)

## 基础知识

##### 基本概念

周期函数 $\varphi(x+T) = \varphi(x)$

正弦型函数  $Asin(\omega t+\varphi)$

##### 三角函数族的正交性

三角函数族 {$1, cos x, sin x, cos 2x, sin 2x, ... ,cos nx, sin nx, ...$}
$$
\int_{-\pi}^{\pi}1 \cdot cos nx dx = \frac{sin nx}{n} |_{-\pi}^{\pi} = 0\\
\int_{-\pi}^{\pi}1 \cdot sin nx dx = -\frac{cos nx}{n} |_{-\pi}^{\pi} = 0\\
\int_{-\pi}^{\pi}cos nx \cdot sin mx dx = \frac{1}{2}\int_{-\pi}^{\pi}[sin(m+n)x + sin(m-n)x ]dx = 0 \\
\int_{-\pi}^{\pi}cos nx \cdot cos mx dx = \frac{1}{2}\int_{-\pi}^{\pi}[cos(n+m)x + cos(n-m)x ]dx = 0, m \neq n \\
\int_{-\pi}^{\pi}sin nx \cdot sin mx dx = \frac{1}{2}\int_{-\pi}^{\pi}[cos(n-m)x - cos(m+n)x ]dx = 0, m \neq n \\
$$

## 推导过程

设三角函数式$\frac{a_0}{2}+\sum_{i=1}^{\infty}(a_n cos nx+b_n sin nx)$，一致收敛到$f(x)$，则
$$
f(x) = \frac{a_0}{2}+\sum_{i=1}^{\infty}(a_n cos nx+b_n sin nx)
$$
考虑
$$
f(x)cos mx = \frac{a_0 cos mx}{2}+\sum_{i=1}^{\infty}(a_n cos nx cos mx+b_n sin nx cos mx)
$$
积分得
$$
\int_{-\pi}^{\pi}f(x)cos mx dx = \int_{-\pi}^{\pi}\frac{a_0 cos mx}{2} dx+\sum_{i=1}^{\infty}(a_n \int_{-\pi}^{\pi}cos nx cos mx dx+b_n\int_{-\pi}^{\pi}sin nx cos mx dx) \\
= \pi a_m
$$
得到
$$
a_m = \frac{1}{\pi}\int_{-\pi}^{\pi}f(x)cos mx dx, m = 0, 1, 2, ...,
$$
同理
$$
b_m = \frac{1}{\pi}\int_{-\pi}^{\pi}f(x)sin mx dx, m = 1, 2, ...,
$$
$f(x) = \frac{a_0}{2}+\sum_{i=1}^{\infty}(a_n cos nx+b_n sin nx)$ 称为$f(x)$的`Fourier`级数

## 收敛条件

至今还没有判断傅里叶级数的收敛性充分必要条件，但是对于实际问题中出现的函数，有很多种判别条件可用于判断收敛性。比如$f(x)$的可微性或级数的一致收敛性。在闭区间上满足狄利克雷条件的函数表示成的傅里叶级数都收敛。狄利克雷条件如下：

1. 在定义区间上，$f(x)$须绝对可积；
2. 在任一有限区间中，$f(x)$只能取有限个极值点；
3. 在任何有限区间上，$f(x)$只能有有限个第一类间断点。

满足以上条件的$f(x)$傅里叶级数都收敛，且：

​	1.当$x$是$f(x)$的连续点时，级数收敛于$f(x)$；

​	2.当$x$是$f(x)$的间断点时，级数收敛于$\frac{1}{2}[f(x^{-})+f(x^{+})]$

## 备注

由傅里叶变换可以得到一些有趣的结论
$$
\frac{1}{1^2}+\frac{1}{3^2}+\frac{1}{5^2}+...=\frac{\pi^2}{8} \\
1-\frac{1}{3}+\frac{1}{5}-\frac{1}{7}+...=\frac{\pi}{4} \\
1+\frac{1}{5}-\frac{1}{7}-\frac{1}{11}+\frac{1}{13}+\frac{1}{17}...=\frac{\pi}{3} \\
1-\frac{1}{5}+\frac{1}{7}-\frac{1}{11}+\frac{1}{13}-\frac{1}{17}...=\frac{\sqrt{3} \pi}{6} \\
\sum_{n=1}^{\infty}\frac{1}{n^2} = \frac{\pi^2}{6} \\
\int_{-\infty}^{+\infty} \frac{sin x}{x} dx = \pi \\
\sum_{n=1}^{\infty} \frac{sin n}{n} = \sum_{n=1}^{\infty} (\frac{sin n}{n})^2 = \frac{\pi - 1}{2} \\
\sum_{n=1}^{\infty} \frac{sin^2 n}{n^4} = \frac{(\pi - 1)^2}{6} \\
$$
