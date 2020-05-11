# 4.1

## この問題の気持ち
順々に考えていかないと難しくなってしまう。わからないときは、累積分布を確率の基礎に立ち返って考えていくことが大切。

今回の問題は、$\varepsilon, X, Y, Z$
と複数の変数が出ているのでわかりにくいが、

コインと二つの袋（赤玉がそれぞれの確率で入っている）があり、
Zを赤玉が出る確率変数。X, Yがそれぞれの赤だまが出るものと考えると。
コインで表が出たらXの方の袋、裏ならばYの方の袋から抽出すると考えるとわかりやすい。


##(1)

$$
\varepsilon \sim Ber(p)
$$
より、


$$
\varepsilon \in (0,1)
$$
コインを投げた後に、そのコインのでかたによって、
Zの確率変数は$\varepsilon$によって条件づけられているので、
$$
P(Z<z) = P(\varepsilon X+(1-\varepsilon)Y<z|\varepsilon=1)P(\varepsilon=1)+P(\varepsilon X+(1-\varepsilon)Y<z|\varepsilon=0)P(\varepsilon=0)\\=P(X<z|\varepsilon=1)p+P(Y<z|\varepsilon=0)(1-p)\\=P(X<z)p+P(Y<z)(1-p)\\(\because (Y,\varepsilon),(X,\varepsilon) がそれぞれ独立 )\\=F_X(z)p+F_{Y}(z)(1-p)
$$

となる。

# 4.2

## この問題の気持ち
ポアソン分布は、本に書いてある通り、再生性を持つので、ポアソン分布になることがわかる。こんな時は、積率母関数を使う

## (1)
$$
X\sim Po(\lambda)\\
E[e^{tX}]=e^{-\lambda}\sum^\infty_{x=0}e^{tx}\frac{\lambda^x}{x!}\\=e^{-\lambda}\sum^\infty_{x=0}\frac{(e^t\lambda )^x}{x!}\\=e^{e^t\lambda - \lambda} = e^{\lambda(e^t-1) }
$$
今回の場合X,Y独立なので、

$$
E[e^{t(X+Y)}]=E[e^{tX}]E[e^{tY}]=e^{\lambda_1(e^t-1) }e^{\lambda_2(e^t-1) }=e^{(\lambda_1+\lambda_2)(e^t-1) }
$$

積率母関数と、分布の一対一対応より、
$$
X+Y\sim Po((\lambda+\mu))
$$

## (2)

$$
P(X=r|X+Y = n) = \frac{P(X=r\cap X+Y=n)}{P(X+Y = n)}\\
=\frac{e^{-\lambda}\frac{\lambda ^r}{r!}e^{-\mu}\frac{\mu ^{n-r}}{(n-r)!}}{e^{-(\lambda+\mu)}\frac{(\lambda+\mu )^n}{n!}}\\=\frac{n!}{r!(n-r)!}\frac{\lambda^r}{(\lambda+\mu)^{r}}\frac{\mu^{n-r}}{(\lambda+\mu)^{n-r}}
$$

$$
p = \frac{\lambda}{(\lambda+\mu)}
$$
とすると、
$$
P(X=r|X+Y = n)={}_nC_rp^r(1-p)^{n-r}
$$

## (3)

上の形を見ると、二項分布だということがわかる。二項分布の平均と分散より、
$$
E^{X|X+Y =n}[X] = np
$$
$$
E^{X|X+Y =n}[X] = np(1-p)
$$

# 4.3

## この問題の気持ち

めんどくさい。うまい方法はあるかもしれない。。。が知識で押す。。\
計算で求められる方法教えてください。
## (1)

はじめに
$$
\mathscr{X}=\frac{(X-np)^2}{np}+\frac{(Y-nq)^2}{nq}+\frac{(Z-nr)^2}{nr}\\=\frac{X^2}{np}+\frac{Y^2}{nq}+\frac{Z^2}{nr}
-n\\=\frac{X^2}{np}+\frac{Y^2}{nq}+\frac{Z^2}{nr}-n\\=X^2(\frac{1}{np}+\frac{1}{nr})+Y^2(\frac{1}{nq}+\frac{1}{nr})+2\frac{XY-nX+nY}{nr}+\frac{n}{r}-n
$$
$$
E[\mathscr{X}]=\sum_{x=0}^n\sum_{y=0}^{n-x}xy\mathscr{X}\\
$$

となるここで、
$$
\sum_{x=0}^n\sum_{y=0}^{n-x}x^3y=
\sum_{x=0}^nx^3\frac{(n-x)(n-x+1)}{2}=\\

\cdots
$$
という感じでゴリゴリ進めることもできるのかなぁ。
これは結構しんどいとおもう。5乗の和も計算しなければならない。。

なので知識で押す。（この問題にもそのページ数が書かれているので、悪くないかもしれない）
この統計量は、自由度n-1の$\chi^2$分布に従うことが知られている。なのでそれに従う。よって、
$$
E[X] = 3-1 = 2\\
V(X) = 2(3-1)=4
$$

# 4.4

## この問題の気持ち

計算しても図を考えても一様分布なので簡単。図のみを乗せとく

# 4.5

## この問題の気持ち
計算だけど、よく知られている分布を想像しつつ。
(1)なんかわガンマ分布だと気づけば計算しなくても簡単。

(1)

$$
\int_{0}^\infty\int_{0}^\infty cx^3exp(-x(1+y))dxdy
$$
ガンマ分布に近いことを考えると(一回積分して、$x^2$になることを考えると)
$$
c = \frac{1}{\Gamma(3)} = \frac{1}{2}
$$
(2)
xに関しては、すぐにガンマ分布であることがわかる。

$$
f_1(x) = \frac{1}{2}x^2exp(-x)
$$

yは計算すると

$$
f_2(y) = \frac{1}{2}\int^{-\infty}_{0}cx^3exp(-x(1+y))dx\\
x(1+y)\rightarrow z\\
f_2(y) = \frac{1}{2}\frac{1}{(1+y)^4}\int^{\infty}_{0}z^3exp(-z)dz\\=f_2(y) = \frac{1}{2}\frac{1}{(1+y)^4}\Gamma(4) \\=\frac{1}{2}\frac{3!}{(1+y)^4}=\frac{3}{(1+y)^4}
$$
(3)

$$
E[X]=\frac{1}{2}\int^\infty_0 x^3 exp(-x)dx = \frac{1}{2}\Gamma(4)=2\\
E[X^2]=\frac{1}{2}\Gamma(5) = 6\\

Var(X) = 6  - 2^2 = 2
$$

$$
E[Y]=\int^\infty_0 \frac{3y}{(1+y)^4}dy \\= 3\left(\int^\infty_0 \frac{1+y}{(1+y)^4}dy - \int^\infty_0 \frac{1}{(1+y)^4}dy\right)\\=3(\frac{1}{2}-\frac{1}{3})=\frac{1}{2}
$$
右の項は上の密度関数と近いことから、すぐにわかる。その流れで左もわかる
$$
\int \frac{1}{(1+y)^n}dy = \frac{1}{n-1}
$$
$$
E[Y^2] = \int^\infty_0 \frac{3y^2}{(1+y)^4}dy \\= 3\left(\int^\infty_0 \frac{(1+y)^2}{(1+y)^4}dy - 2\int^\infty_0 \frac{y}{(1+y)^4}dy-\int^\infty_0 \frac{1}{(1+y)^4}dy\right)\\=3(1-\frac{1}{3}-\frac{1}{3})=1\\
Var(Y)=\frac{3}{4}
$$

$$
E[XY] =\frac{1}{2}\int_{0}^\infty\int_{0}^\infty x^4yexp(-x(1+y))dydx\\=\frac{1}{2}\int_{0}^\infty\int_{0}^\infty x^4yexp(-x(1+y))dydx\\=\frac{1}{2}\int_{0}^\infty\int_{0}^\infty x^3(\frac{z}{x}-1)exp(-z)dzdx\\=\frac{1}{2}\int_{0}^\infty\left(\int_{0}^\infty x^2zexp(-z)dz-\int_{0}^\infty x^3exp(-z)dz\right)dx\\=\frac{1}{2}\int_{0}^\infty\left(x^2+ x\right)dx=\frac{1}{2}[1/3x^3+1/2x^2]^\infty_0
$$
