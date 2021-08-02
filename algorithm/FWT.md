



回忆一下多项式的卷积
$$
C_k = \sum_{i+j=k} A_i * B_j
$$


我们可以用`FFT`来做。

甚至在一些特殊情况下，我们$C_k = \sum_{i*j=k} A_i * B_j$也能做（SDOI2015 序列统计）。

但是，如果我们把操作符换一下呢？

比如这样？

$$
C_k=\sum_{i|j=k}A_i*B_j \\

C_k=\sum_{i\&j=k}A_i*B_j \\ 

C_k=\sum_{i\wedge j=k}A_i*B_j
$$


似乎这就不能用`FFT`来做了。

这样子就有了`FWT`——用来解决多项式的位运算卷积