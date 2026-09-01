---
title: 微分、切向量与余切向量
date: 2026-09-01
category: 微分几何
description: 从曲线速度出发，理解切空间、余切空间、微分以及它们之间的自然配对。
---

## 1. 从欧氏空间中的切向量说起

在微积分中，曲线的导数给出它的瞬时速度，也就是切向量。设

$$
\gamma:(-\varepsilon,\varepsilon)\to\mathbb R^n,
\qquad
\gamma(t)=\bigl(x^1(t),\ldots,x^n(t)\bigr),
\qquad \gamma(0)=p,
$$

则曲线在 $p$ 处的速度为

$$
\gamma'(0)=
\left(\frac{dx^1}{dt}(0),\ldots,\frac{dx^n}{dt}(0)\right).
$$

对于局部参数曲面

$$
\mathbf r=\mathbf r(u,v),
$$

若曲面上的曲线写成

$$
\gamma(t)=\mathbf r\bigl(u(t),v(t)\bigr),
$$

那么由链式法则，

$$
\gamma'(0)
=
\mathbf r_u\bigl(u(0),v(0)\bigr)u'(0)
+
\mathbf r_v\bigl(u(0),v(0)\bigr)v'(0).
$$

因此，曲面的切向量是 $\mathbf r_u,\mathbf r_v$ 的线性组合。

但是这种定义有两个局限：

1. 一般流形没有预先选定的全局坐标；
2. 一般流形不必被看成某个欧氏空间的子集，所以不能依赖环境空间来定义切向量。

我们需要一个不依赖特定坐标和嵌入的定义。

## 2. 经过一点的曲线与函数芽

设 $M$ 是 $n$ 维光滑流形，$p\in M$。记

$$
\Gamma_p
=
\left\{
\gamma:(-\varepsilon,\varepsilon)\to M
\ \middle|\
\gamma\text{ 光滑且 }\gamma(0)=p
\right\}.
$$

$\Gamma_p$ 是所有经过 $p$ 的局部光滑曲线的集合。

为了只保留函数在 $p$ 附近的信息，引入函数芽。若 $f,g$ 分别定义在 $p$ 的某个邻域上，定义

$$
f\sim_p g
\quad\Longleftrightarrow\quad
\text{存在 }p\text{ 的邻域 }W,\text{ 使 }f|_W=g|_W.
$$

这是等价关系：

- 自反性显然；
- 若 $f=g$ 于 $W$，则 $g=f$ 于 $W$，故有对称性；
- 若 $f=g$ 于 $W_1$、$g=h$ 于 $W_2$，则 $f=h$ 于仍含 $p$ 的邻域 $W_1\cap W_2$，故有传递性。

$f$ 的等价类记为 $[f]_p$，称为 $f$ 在 $p$ 处的芽。所有光滑函数芽组成的向量空间记为 $\mathcal F_p$。不致混淆时简写为 $[f]$。

## 3. 曲线测量函数的一阶变化

对 $\gamma\in\Gamma_p$ 和 $[f]\in\mathcal F_p$，定义

$$
D_\gamma[f]
:=
\langle\gamma,[f]\rangle
:=
\left.\frac{d}{dt}(f\circ\gamma)(t)\right|_{t=0}.
\tag{3.1}
$$

### 命题 3.1：定义 (3.1) 是良定的

**证明。** 若 $[f]=[g]$，则存在 $p$ 的邻域 $W$，使 $f=g$ 于 $W$。由于 $\gamma(0)=p$ 且 $\gamma$ 连续，存在 $\delta>0$，使 $|t|<\delta$ 时 $\gamma(t)\in W$。于是 $t=0$ 附近有

$$
f\circ\gamma=g\circ\gamma,
$$

从而

$$
\left.\frac{d}{dt}(f\circ\gamma)(t)\right|_0
=
\left.\frac{d}{dt}(g\circ\gamma)(t)\right|_0.
$$

所以结果只依赖函数芽，与代表元的选择无关。 $\square$

对固定的 $\gamma$，映射

$$
D_\gamma:\mathcal F_p\to\mathbb R
$$

是线性的，并且满足莱布尼茨法则

$$
D_\gamma(fg)
=
f(p)D_\gamma g+g(p)D_\gamma f.
\tag{3.2}
$$

这由一元函数的乘积求导公式直接得到。因此，曲线在 $p$ 处的速度可以看成“对所有光滑函数求方向导数”的算子。

## 4. 余切空间：函数的一阶信息

有些函数芽沿任意经过 $p$ 的曲线都没有一阶变化。定义

$$
\mathcal Z_p
=
\left\{
[f]\in\mathcal F_p
\ \middle|\
D_\gamma[f]=0,\ \forall\gamma\in\Gamma_p
\right\}.
\tag{4.1}
$$

### 命题 4.1：$\mathcal Z_p$ 是线性子空间

**证明。** 显然 $[0]\in\mathcal Z_p$。若 $[f],[g]\in\mathcal Z_p$，且 $a,b\in\mathbb R$，那么对任意 $\gamma\in\Gamma_p$，

$$
D_\gamma[af+bg]
=aD_\gamma[f]+bD_\gamma[g]
=0.
$$

故 $[af+bg]\in\mathcal Z_p$。 $\square$

定义 $p$ 处的余切空间为商空间

$$
T_p^*M:=\mathcal F_p/\mathcal Z_p.
\tag{4.2}
$$

$[f]$ 在该商空间中的等价类记为

$$
(df)_p\quad\text{或}\quad df_p,
$$

称为 $f$ 在 $p$ 处的微分。因此

$$
df_p=dg_p
\quad\Longleftrightarrow\quad
[f-g]\in\mathcal Z_p.
$$

换言之，$df_p=dg_p$ 当且仅当 $f$ 和 $g$ 沿每一条经过 $p$ 的光滑曲线都有相同的一阶变化率。

## 5. 局部坐标中的余切空间

取包含 $p$ 的局部坐标卡

$$
(U,x),\qquad
x=(x^1,\ldots,x^n):U\to x(U)\subset\mathbb R^n,
$$

令 $a=x(p)$。对定义在 $p$ 附近的函数 $f$，记其坐标表示为

$$
F=f\circ x^{-1}.
$$

对任意 $\gamma\in\Gamma_p$，链式法则给出

$$
D_\gamma[f]
=
\sum_{i=1}^n
\frac{\partial F}{\partial x^i}(a)
\left.\frac{d(x^i\circ\gamma)}{dt}\right|_{t=0}.
\tag{5.1}
$$

### 命题 5.1：$\mathcal Z_p$ 的坐标判别法

$$
[f]\in\mathcal Z_p
\quad\Longleftrightarrow\quad
\frac{\partial F}{\partial x^i}(a)=0,
\qquad i=1,\ldots,n.
\tag{5.2}
$$

**证明。**

若所有一阶偏导数都为零，则由 (5.1)，对任意 $\gamma\in\Gamma_p$ 都有 $D_\gamma[f]=0$，故 $[f]\in\mathcal Z_p$。

反之，对每个 $i$ 取坐标直线

$$
\gamma_i(t)=x^{-1}(a+te_i),
\tag{5.3}
$$

其中 $e_i$ 是 $\mathbb R^n$ 的第 $i$ 个标准基向量。若 $[f]\in\mathcal Z_p$，则

$$
0
=D_{\gamma_i}[f]
=\left.\frac{d}{dt}F(a+te_i)\right|_{t=0}
=\frac{\partial F}{\partial x^i}(a).
$$

所以所有一阶偏导数都为零。 $\square$

对坐标函数 $x^i$，其在 $p$ 处的微分记为 $dx_p^i$。

### 命题 5.2：$\{dx_p^1,\ldots,dx_p^n\}$ 是 $T_p^*M$ 的一组基

**证明。**

先证生成性。对任意 $df_p$，令

$$
c_i=\frac{\partial F}{\partial x^i}(a),
\qquad
h=f-\sum_{i=1}^n c_i x^i.
$$

则

$$
\frac{\partial(h\circ x^{-1})}{\partial x^j}(a)
=
\frac{\partial F}{\partial x^j}(a)-c_j
=0.
$$

由命题 5.1，$[h]\in\mathcal Z_p$，所以 $dh_p=0$。因此

$$
df_p
=
\sum_{i=1}^n
\frac{\partial F}{\partial x^i}(a)\,dx_p^i.
\tag{5.4}
$$

再证线性无关。若

$$
\sum_{i=1}^n c_i\,dx_p^i=0,
$$

用 (5.3) 中的坐标曲线 $\gamma_j$ 测量，得到

$$
0
=
\left\langle\gamma_j,\sum_{i=1}^n c_i\,dx_p^i\right\rangle
=c_j.
$$

对每个 $j$ 都有 $c_j=0$，所以这组余切向量线性无关。 $\square$

由此

$$
\dim T_p^*M=n.
$$

公式 (5.4) 就是熟悉的全微分公式。这里的 $dx_p^i$ 不是“无穷小数”，而是余切空间中的基向量。

## 6. 由曲线定义切向量

对 $\gamma\in\Gamma_p$ 和 $df_p\in T_p^*M$，定义

$$
\langle\gamma,df_p\rangle
:=
D_\gamma[f]
=
\left.\frac{d}{dt}(f\circ\gamma)(t)\right|_{t=0}.
\tag{6.1}
$$

该定义对 $df_p$ 是良定的：若 $df_p=dg_p$，则 $[f-g]\in\mathcal Z_p$，故对任意 $\gamma$，

$$
D_\gamma[f-g]=0,
$$

即 $D_\gamma[f]=D_\gamma[g]$。

不同曲线可能对所有余切向量都给出相同的测量结果。因此在 $\Gamma_p$ 上定义

$$
\gamma\sim\eta
\quad\Longleftrightarrow\quad
\langle\gamma,\omega\rangle
=
\langle\eta,\omega\rangle,
\qquad \forall\omega\in T_p^*M.
\tag{6.2}
$$

这是等价关系，因为实数相等具有自反性、对称性和传递性，且这些性质对每个 $\omega$ 同时成立。

曲线 $\gamma$ 的等价类记为 $[\gamma]$，定义

$$
T_pM:=\Gamma_p/\!\sim.
\tag{6.3}
$$

$T_pM$ 称为 $M$ 在 $p$ 处的切空间，其元素 $[\gamma]$ 称为切向量。

切向量不是一条具体曲线，而是所有具有相同一阶速度的曲线组成的等价类。

## 7. 曲线等价等同于坐标速度相等

在坐标 $x=(x^1,\ldots,x^n)$ 中，定义曲线的坐标速度

$$
\dot x_\gamma(0)
=
\left(
\left.\frac{d(x^1\circ\gamma)}{dt}\right|_0,
\ldots,
\left.\frac{d(x^n\circ\gamma)}{dt}\right|_0
\right).
$$

### 命题 7.1

$$
\gamma\sim\eta
\quad\Longleftrightarrow\quad
\dot x_\gamma(0)=\dot x_\eta(0).
\tag{7.1}
$$

**证明。**

若两条曲线的坐标速度相同，则由 (5.1)，对任意光滑函数 $f$，

$$
\begin{aligned}
D_\gamma[f]
&=
\sum_i\frac{\partial F}{\partial x^i}(a)
\left.\frac{d(x^i\circ\gamma)}{dt}\right|_0\\
&=
\sum_i\frac{\partial F}{\partial x^i}(a)
\left.\frac{d(x^i\circ\eta)}{dt}\right|_0
=D_\eta[f].
\end{aligned}
$$

所以 $\gamma\sim\eta$。

反之，若 $\gamma\sim\eta$，依次选取 $f=x^i$，得到

$$
\left.\frac{d(x^i\circ\gamma)}{dt}\right|_0
=
\left.\frac{d(x^i\circ\eta)}{dt}\right|_0,
\qquad i=1,\ldots,n.
$$

所以两条曲线的坐标速度相同。 $\square$

于是映射

$$
\Psi_x:T_pM\to\mathbb R^n,
\qquad
[\gamma]\longmapsto\dot x_\gamma(0)
\tag{7.2}
$$

是单射。它也是满射：对任意 $c=(c^1,\ldots,c^n)\in\mathbb R^n$，取

$$
\gamma_c(t)=x^{-1}(a+tc),
$$

就有 $\dot x_{\gamma_c}(0)=c$。因此 $\Psi_x$ 是双射。

利用这个双射，可将 $\mathbb R^n$ 的向量空间结构转移到 $T_pM$ 上，从而 $T_pM$ 是 $n$ 维向量空间。

## 8. 切空间与余切空间的对偶

对 $v=[\gamma]\in T_pM$ 和 $\omega=df_p\in T_p^*M$，定义

$$
\langle v,\omega\rangle
:=
\langle\gamma,df_p\rangle.
\tag{8.1}
$$

由两侧的等价关系，这个配对对 $v$ 和 $\omega$ 都是良定的。对固定的 $v$，映射

$$
\omega\longmapsto\langle v,\omega\rangle
$$

是 $T_p^*M$ 上的线性函数，因此得到自然线性映射

$$
\Phi:T_pM\to(T_p^*M)^*,
\qquad
\Phi(v)(\omega)=\langle v,\omega\rangle.
$$

### 命题 8.1：$\Phi$ 是同构

**证明。**

若 $\Phi([\gamma])=\Phi([\eta])$，则二者对每个 $\omega\in T_p^*M$ 的取值相同。由曲线等价关系的定义，$\gamma\sim\eta$，故 $[\gamma]=[\eta]$。所以 $\Phi$ 是单射。

为证满射，取 $\Lambda\in(T_p^*M)^*$，令

$$
c^i=\Lambda(dx_p^i).
$$

由于 $\{dx_p^i\}$ 是 $T_p^*M$ 的基，$\Lambda$ 完全由这些数决定。取

$$
\gamma(t)=x^{-1}\bigl(a+t(c^1,\ldots,c^n)\bigr).
$$

则

$$
\Phi([\gamma])(dx_p^i)=c^i=\Lambda(dx_p^i).
$$

两个线性函数在一组基上的值相同，所以 $\Phi([\gamma])=\Lambda$。因此 $\Phi$ 满射。 $\square$

于是可以自然地写成

$$
T_pM\cong(T_p^*M)^*.
\tag{8.2}
$$

## 9. 坐标基与配对公式

令

$$
\gamma_i(t)=x^{-1}(a+te_i),
$$

定义切空间的自然基

$$
\left.\frac{\partial}{\partial x^i}\right|_p
:=[\gamma_i].
$$

任意 $v=[\gamma]\in T_pM$ 可写成

$$
v
=
\sum_{i=1}^n
v^i
\left.\frac{\partial}{\partial x^i}\right|_p,
\qquad
v^i=
\left.\frac{d(x^i\circ\gamma)}{dt}\right|_0.
\tag{9.1}
$$

任意函数的微分写成

$$
df_p
=
\sum_{i=1}^n
\frac{\partial F}{\partial x^i}(a)\,dx_p^i.
\tag{9.2}
$$

两组基互为对偶基：

$$
dx_p^j
\left(
\left.\frac{\partial}{\partial x^i}\right|_p
\right)
=\delta_i^j.
\tag{9.3}
$$

因此

$$
df_p(v)
=
\langle v,df_p\rangle
=
\sum_{i=1}^n
\frac{\partial F}{\partial x^i}(a)v^i.
\tag{9.4}
$$

这就是曲线求导、切向量与函数微分之间的基本关系。

## 10. 坐标无关性

设 $y=(y^1,\ldots,y^n)$ 是 $p$ 附近的另一套坐标。对 $v=[\gamma]$，链式法则给出

$$
\left.\frac{d(y^\alpha\circ\gamma)}{dt}\right|_0
=
\sum_{i=1}^n
\frac{\partial y^\alpha}{\partial x^i}(p)
\left.\frac{d(x^i\circ\gamma)}{dt}\right|_0.
\tag{10.1}
$$

所以切向量分量满足

$$
v_y^\alpha
=
\sum_i
\frac{\partial y^\alpha}{\partial x^i}(p)v_x^i.
$$

切向量基满足

$$
\left.\frac{\partial}{\partial x^i}\right|_p
=
\sum_\alpha
\frac{\partial y^\alpha}{\partial x^i}(p)
\left.\frac{\partial}{\partial y^\alpha}\right|_p,
$$

余切基满足

$$
dx_p^i
=
\sum_\alpha
\frac{\partial x^i}{\partial y^\alpha}(p)\,dy_p^\alpha.
$$

坐标分量会改变，但切向量、余切向量和配对 $df_p(v)$ 本身不变。坐标只是这些内在几何对象的表示工具。

## 11. 光滑映射的微分

设

$$
G:M\to N
$$

是光滑映射。对 $v=[\gamma]\in T_pM$，定义

$$
dG_p(v):=[G\circ\gamma]\in T_{G(p)}N.
\tag{11.1}
$$

### 命题 11.1：$dG_p$ 是良定的

**证明。** 若 $[\gamma]=[\eta]$，需证明 $[G\circ\gamma]=[G\circ\eta]$。对 $N$ 上 $G(p)$ 附近的任意光滑函数 $h$，

$$
\begin{aligned}
\left.\frac{d}{dt}h(G(\gamma(t)))\right|_0
&=D_\gamma[h\circ G]\\
&=D_\eta[h\circ G]\\
&=\left.\frac{d}{dt}h(G(\eta(t)))\right|_0.
\end{aligned}
$$

所以 $G\circ\gamma\sim G\circ\eta$，定义与代表曲线无关。 $\square$

在坐标中，$dG_p$ 由 $G$ 的雅可比矩阵表示。欧氏空间中的全导数正是流形之间微分的坐标表达。

## 12. 三种等价观点

在有限维光滑流形上，以下三种对象描述同一个切向量：

1. **曲线速度**：经过 $p$ 的曲线的一阶等价类 $[\gamma]$；
2. **导子**：作用在光滑函数芽上、满足莱布尼茨法则的线性算子 $v(f)$；
3. **坐标分量**：局部坐标中的数组 $(v^1,\ldots,v^n)$，换坐标时按雅可比矩阵变换。

它们分别突出几何、代数和计算三个方面。

这三种观点确实等价。曲线类 $[\gamma]$ 通过

$$
v_\gamma(f)
:=
\left.\frac{d}{dt}(f\circ\gamma)(t)\right|_0
$$

给出满足莱布尼茨法则的导子。反过来，若 $D:\mathcal F_p\to\mathbb R$ 是满足莱布尼茨法则的线性导子，在坐标 $x=(x^1,\ldots,x^n)$ 中令

$$
v^i:=D(x^i).
$$

由多元函数在 $a=x(p)$ 处的一阶展开，

$$
F(z)-F(a)
=
\sum_{i=1}^n(z^i-a^i)F_i(z),
\qquad
F_i(a)=\frac{\partial F}{\partial x^i}(a),
$$

以及莱布尼茨法则，可得

$$
D(f)
=
\sum_{i=1}^n
v^i\frac{\partial F}{\partial x^i}(a).
$$

因此 $D$ 正是坐标分量为 $(v^1,\ldots,v^n)$ 的切向量；取曲线

$$
\gamma(t)=x^{-1}\bigl(a+t(v^1,\ldots,v^n)\bigr)
$$

即可实现这个导子。

## 13. 核心结论

$$
\boxed{
\begin{aligned}
\text{切向量 }v
&=\text{曲线在一点的一阶运动信息},\\
\text{余切向量 }\omega
&=\text{测量切向量的线性函数},\\
df_p(v)
&=\text{函数 }f\text{ 沿方向 }v\text{ 的一阶变化率}.
\end{aligned}
}
$$

参数 $t$ 只是通过曲线提取瞬时速度的工具。将曲线按一阶速度取等价类以后，切向量 $[\gamma]$、余切向量 $df_p$ 和配对 $df_p(v)$ 都是与具体代表曲线无关的内在几何对象。
