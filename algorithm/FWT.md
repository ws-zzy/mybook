$$C_k=\sum_{i|j=k}A_i*B_j$$

$$C_k=\sum_{i\&j=k}A_i*B_j$$

$$C_k=\sum_{i\wedge j=k}A_i*B_j$$



回忆一下多项式的卷积Ck=∑i+j=kAi∗BjCk=∑i+j=kAi∗Bj

我们可以用FFTFFT来做。

甚至在一些特殊情况下，我们Ck=∑i∗j=kAi∗BjCk=∑i∗j=kAi∗Bj也能做（SDOI2015 序列统计）。

但是，如果我们把操作符换一下呢？

比如这样？

Ck=∑i|j=kAi∗BjCk=∑i|j=kAi∗Bj

Ck=∑i&j=kAi∗BjCk=∑i&j=kAi∗Bj

Ck=∑i∧j=kAi∗BjCk=∑i∧j=kAi∗Bj

似乎这就不能用FFTFFT来做了。

这样子就有了FWTFWT——用来解决多项式的位运算卷积