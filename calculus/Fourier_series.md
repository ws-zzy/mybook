在数学中，**傅里叶级数**（**fourier series**，[/ˈfʊrieɪ, -iər/]）是把类似波的函数表示成简单正弦波的方式。更正式地说，它能将任何周期函数或周期信号分解成一个（可能由无穷个元素组成的）简单振荡函数的集合，即正弦函数和余弦函数（或者，等价地使用[复指数](https://zh.wikipedia.org/wiki/复指数)

## 基础知识

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


至今还没有判断傅里叶级数的收敛性充分必要条件，但是对于实际问题中出现的函数，有很多种判别条件可用于判断收敛性。比如x(t)的可微性或级数的[一致收敛性](https://zh.wikipedia.org/wiki/一致收敛)。在闭区间上满足[狄利克雷](https://zh.wikipedia.org/wiki/狄利克雷)条件的函数表示成的傅里叶级数都收敛。狄利克雷条件如下：

1. 在定义区间上，x(t)须[绝对可积](https://zh.wikipedia.org/wiki/绝对可积)；
2. 在任一有限区间中，x(t)只能取有限个极值点；
3. 在任何有限区间上，x(t)只能有有限个[第一类间断点](https://zh.wikipedia.org/w/index.php?title=第一类间断点&action=edit&redlink=1)。

满足以上条件的x(t)傅里叶级数都收敛，且：

1.当t是x(t)的连续点时，级数收敛于x(t)；

2.当t是x(t)的间断点时，级数收敛于$\frac{1}{2}[x(t^{-})+x(t^{+})]$