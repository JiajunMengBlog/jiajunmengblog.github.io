## 分部积分法

$$
\int_a^bud\nu=(u\nu)\Big|_a^b-\int_a^b\nu du
$$

## 包络定理

<u>Definition</u>: 参数的值变动时，目标函数的变动只和参数的变动有关，而与自变量（因参数变动而引起）的变动无关

- 设目标函数 $f(x, α)$ 是可微实函数，其中 $x$ 是自变量,  $α$ 是参数。设 $V(α)=f(x^∗,α)$，其中 $x^∗$ 是 $f$ 取到极值时的 $x$*，*则包络定理指出

$$
\frac{\mathrm{d}V}{\mathrm{d}\alpha}=\frac{\partial f}{\partial\alpha}\Bigg|_{x=x^*}
$$

<u>Proof</u>: 根据全微分公式
$$
\mathrm{d}V=\mathrm{d}f\Big|_{x=x^*}=\left(\frac{\partial f}{\partial x}\mathrm{d}x+\frac{\partial f}{\partial\alpha}\mathrm{d}\alpha\right)\Big|_{x=x^*}
$$
因为 $x^∗$ 是 $f$ 取到极值时的 $x$, 故 $\frac{\partial f}{\partial x}\Big|_{x=x^*}=0$. 因此，$\mathrm{d}V=\frac{\partial f}{\partial\alpha}\mathrm{d}\alpha|_{x=x^*}$， 即$\frac{\mathrm{d}V}{\mathrm{d}\alpha}=\frac{\partial f}{\partial\alpha}\Big|_{x=x^*}$.               Q.E.D.

## 全微分

<u>Definition</u>: 在微积分中，函数在某一点的全微分是指该函数在该点附近关于其自变量的最佳线性近似。与偏微分不同，全微分反映了函数关于其所有自变量的线性近似，而非单个自变量

- 若函数 $z=f(x,y)$ 在点 $(x,y)$ 可微分，则该函数在点 $(x,y)$ 的偏导数 $∂z/∂x$, $∂z/∂y$ 必然存在，且函数 $z=f(x,y)$ 在点 $(x,y)$ 的全微分为

$$
\mathrm{d}z=\frac{\partial z}{\partial x}\mathrm{d}x+\frac{\partial z}{\partial y}\mathrm{d}y
$$

全微分（d）和偏微分（∂）的区别参考：https://docs.pingcode.com/ask/304438.html 

### 全微分的应用 （Jiang and zou 2020）

<img src="/Users/super/Library/Application Support/typora-user-images/image-20241008152701492.png" alt="image-20241008152701492" style="zoom:75%;" />

用 $x$ 表示 $π^P$ , 则 
$$
d\left(\frac{\partial x}{\partial r}|_{r=r^*}\right)=\left(\frac{\partial\left(\frac{\partial x}{\partial r}\right)}{\partial r}dr+\frac{\partial\left(\frac{\partial x}{\partial r}\right)}{\partial m}dm\right)\Bigg|_{r=r^*}=\frac{\partial^2x}{\partial r^2}\Bigg|_{r=r^*}dr^*+\frac{\partial^2x}{\partial r\partial m}\Bigg|_{r=r^*}dm
$$
因此，
$$
\frac{d\left(\frac{\partial x}{\partial r}|_{r=r^{*}}\right)}{dm}=\frac{\partial^{2}x}{\partial r^{2}}\Big|_{r=r^{*}}\frac{dr^{*}}{dm}+\frac{\partial^{2}x}{\partial r\partial m}\Big|_{r=r^{*}}
$$


## Discrete choice model

<u>Definition</u>: consider an individual who has **to choose a single alternative from a finite choice set of alternatives** **A** (e.g., A could be a set of differentiated products). This does not imply that the individual is forced to choose a “genuine” alternative (e.g., coffee, tea. or milk). Indeed one can add an element to the choice set A, called the **outside alternative**, which corresponds to the option “none of the above” (so A becomes {coffee, tea, milk, none of the above}). 

- **binary** discrete choice model (n=2)
- **multinomial** discrete choice model (n≥2)

### Multinomial discrete choice model

We now derive the choice probabilities in the multinomial discrete choice model. 

Consider the case where there are $n≥2$ alternatives and n random variables (i.i.d.) $ε_1,…,ε_n$ whose cumulative distribution is $F(x)$ and probability distribution is $f(x)$, the utility associated with alternative i is 
$$
U_i=u_i+ε_i
$$

- The utility function $U$ can be decomposed into two parts: $u_i$ represents the known (observable) part, and $ε_i$ represents unknown (unobservable) part

Thus, for any given realization $x$ of $ε_i$, alternative $i$ will be chosen with probability density $\prod_{j\neq i}F(u_i-u_j+x)$.

Accounting for all possible realizations (i.e., $x$), we have
$$
\mathbb{P}_A(i)=\int_{-\infty}^{+\infty}f(x)\prod_{j\neq i}F(u_i-u_j+x) dx
$$

- 为什么有 random variables 这一项，是为了解释消费者在同样情况下却有时会做出不同选择的现象。这说明消费者并不能观察到所有信息从而在所有相同情况下做出那个效用最高的相同选择，因此在建模时加上了一项随机项，代表无法观察到的信息。也正因消费者在同样情况下却有时会做出不同选择，我们用概率 $\mathbb{P}_A (i)$ 表示消费者的选择

### Multinomial logit model (MNL)

Specify the distribution of the random variables $ε_i$ to the **double exponential** **distribution** **(**also called **gumbel** **distribution** or **laplace** **distribution)**, and then generate the MNL

<strong style="color:red;"><u>Theorem (Holman and Maryley)</u></strong>: *Assume* *that* *the* $ε_i$ *are* *i.i.d.* *according* *to* *the* *double exponential* *distribution* $F(x)=\mathbb{P}(\varepsilon_i\leq x)=e^{-e^{-(\frac x\mu+\gamma)}}$, *where* $γ$ *is* *Euler’s* *constant* *($γ≈0.5772$*)* *and* $μ$ *is* *a* *positive* *scale* *parameter.* *Then* *the* *resulting* *choice* *probabilities* *are* *given* *by* 
$$
\mathbb{P}_A(i)=\frac{e^{\frac{u_i}\mu}}{\sum_{j=1}^ne^{\frac{u_j}\mu}}
$$

- $\mathbb{P}_A(i)$ is the *probability* *that* *consumer* *buys* *from* *seller* $i$
- $\frac{e^{\frac{u_i}\mu}}{\sum_{j=1}^ne^{\frac{u_j}\mu}}$ 其实就是Parallel search里面消费者购买产品i的概率, 把 $u_i$ 换成 $u_i-p_i$ 就一模一样了
- In other words, if the $ε_i$ follow a double exponential distribution with mean zero and variance $μ^2 π^2/6$, then the choice probabilities are given by the multinomial logit model 
- p. 39, Anderson et al. 1992

<u>Proof</u>: Beacuse $F(u_i-u_j+x)=e^{-e^{-(\frac{u_i-u_j+x}\mu+\gamma)}}$, thus the density function is given by $f(x)=\frac1\mu e^{-(\frac x\mu+\gamma)}e^{-e^{-(\frac x\mu+\gamma)}}$. Using the change of variables $\delta=e^{-(\frac{x}{\mu}+\gamma)}$ and $y_{j}=e^{\frac{u_{j}}{\mu}}$, we have
$$
\begin{gathered}
\mathbb{P}_A(i) =\int_{-\infty}^{+\infty}f(x)\prod_{j\neq i}F(u_i-u_j+x)dx\stackrel{(a)}{=}\int_{+\infty}^0-e^{-\delta}\prod_{j\neq i}e^{-\frac{\delta y_j}{y_i}}d\delta \\
=\int_{0}^{+\infty}e^{-\delta}\prod_{j\neq i}e^{-\frac{\delta y_j}{y_i}}d\delta=\int_{0}^{+\infty}e^{-\delta(\sum_{j=1}^{n}\frac{y_j}{y_i})}d\delta 
\end{gathered}
$$

- where (a) is because as $x$ approaches infinity, $δ$ approaches zero, and as $x$ approaches negative infinity, $δ$ becomes infinitely large

Integrating, we obtain
$$
\mathbb{P}_A(i)=-\frac{y_i}{\sum_{j=1}^ny_j}e^{-\delta\left(\sum_{j=1}^n\frac{y_j}{y_i}\right)}\Bigg|_0^{+\infty}=\frac{y_i}{\sum_{j=1}^ny_j}=\frac{e^{\frac{u_i}\mu}}{\sum_{j=1}^ne^{\frac{u_j}\mu}}
$$

### $\mathbb{E}[\max_{i=1...n}\{U_i\}]$: expected value of the maximum of $U_i$

Since the $ε_i$ are i.i.d., the distribution function of $\max_{i=1...n}\{U_i\}=\max_{i=1...n}\{u_i+ε_i\}$ is equal to 
$$
H(x)=\prod_{i=1}^nF(x-u_i)
$$

- From $\mathbb{P}(u_1+\varepsilon_1<x)\cdot\mathbb{P}(u_2+\varepsilon_2<x)\cdot...\cdot\mathbb{P}(u_n+\varepsilon_n<x)$

So $H(x)=\prod_{i=1}^ne^{-e^{-(\frac{x-u_i}\mu+\gamma)}}=\prod_{i=1}^ne^{-ke^{-(\frac{x-u_i}\mu)}}=e^{-kLe^{-\frac x\mu}}$, where $k=e^{-\gamma},L=\sum_{i=1}^ne^{\frac{u_i}\mu}$. 

Thus, $h(x)=\frac k\mu LH(x)e^{-\frac x\mu}=\frac k\mu Le^{-kLe^{-\frac x\mu}}e^{-\frac x\mu}$.Thus, $\mathbb{E}\left[\max_{i=1...n}\{U_i\}\right]=\int_{-\infty}^{+\infty}xh(x)dx$. Using the change of variable $t=e^{-\frac x\mu}$ yields
$$
\begin{gathered}
\mathbb{E}\left[\max_{i=1...n}\{U_i\}\right]=\int_{-\infty}^{+\infty}x\frac{k}{\mu}Le^{-kLe^{-\frac{x}{\mu}}}e^{-\frac{x}{\mu}}dx=\int_{+\infty}^0-\mu ln(t)\frac{k}{\mu}Le^{-kLt}t d\big(-\mu ln(t)\big) \\
=\mu\int_{+\infty}^0e^{-kLt}kLln(t) dt=-\mu kL\int_0^{+\infty}e^{-kLt}ln(t) dt \\
\overset{(a)}{\operatorname*{=}}\mu[ln(kL)+\gamma]=\mu\left[ln\left(e^{-\gamma}\sum_{i=1}^ne^{\frac{u_i}\mu}\right)+\gamma\right]=\mu ln\left(\sum_{i=1}^ne^{\frac{u_i}\mu}\right) 
\end{gathered}
$$

- where (a) is from Laplace transform of natural log of $t$, see next subsubsection for more details

- <strong style="color:red;"><u>$\mathrm{If~}u_1=\cdots=u_n=v-p,\mathrm{~then~}\mathbb{E}\left[\max_{i=1...n}\{U_i\}\right]=\mu\mathrm{~}ln(ne^{\frac{v-p}\mu})=v-p+\mu\mathrm{~}ln(n)$</u></strong>
- <strong style="color:red;">If an outside option $U_0=u_0+\varepsilon_0$ exists, and $u_1=\cdotp\cdotp\cdotp=u_n=v-p,u_0=v_0$, then $\mathbb{E}\left[\max_{i=1...n}\{U_i,U_0\}\right]=\mu\operatorname{ln}\left(ne^{\frac{v-p}\mu}+e^{\frac{v_0}\mu}\right)$</strong>
- <strong style="color:red;">$\mathbb{E}[\max_{i=1...n}\{U_i\}]$ 其实就是Parallel search里面的消费者剩余（n个产品里面效用最大的产品效用的期望）$</strong>

#### Laplace transform of natural log of $t$

The Laplace transform is defined (for suitable functions $f$) by $\mathcal{L}(f(t))=F(s)$, that is, $F(s)=\int_{0}^{\infty}e^{-st}f(t) dt$

<u>Definition</u>: Laplace transform of natural log of $t$ is
$$
\mathcal{L}(\ln(t))=\int_0^\infty e^{-st}lnt dt=-\frac{\ln(s)+\gamma}s
$$
<u>Proof</u>: let $\tau=st$, then we have
$$
\begin{aligned}
&\mathcal{L}(\ln(t))=\int_{0}^{\infty}e^{-st}lnt dt \\
&=\int_{0}^{\infty}e^{-\tau}\ln(\frac{\tau}{s}) d(\frac{\tau}{s}) \\
&=\frac{1}{s}\left\lfloor\int_{0}^{\infty}e^{-\tau}\ln(\tau) d(\tau)-\int_{0}^{\infty}e^{-\tau}\ln(s) d(\tau)\right\rfloor \\
&=\frac{1}{s}(-\gamma-\ln(s))
\end{aligned}
$$

- Note: see [https://en.wikipedia.org/wiki/Euler%27s_constant](https://en.wikipedia.org/wiki/Euler's_constant) for why $\int_0^\infty e^{-\tau}\ln(\tau) d(\tau)=-\gamma $