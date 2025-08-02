# 分布定数回路

## 線路の一次定数

![分布定数回路](img/2cables.svg)

単位長当たりの直列インピーダンス $Z = R + j\omega L$ および並列アドミタンス $Y = G + j\omega C$ を持つケーブルを考えると、電信方程式

$$
\begin{cases}
  \dfrac{\partial^2v}{\partial x^2} = LC\dfrac{\partial^2v}{\partial t^2} + (GL + RC)\dfrac{\partial v}{\partial t} + GRv \cr
  \dfrac{\partial^2i}{\partial x^2} = LC\dfrac{\partial^2i}{\partial t^2} + (GL + RC)\dfrac{\partial i}{\partial t} + GRv
\end{cases}
$$

において、仮定より

$$
\begin{cases}
  \dfrac{dV}{dx} + ZI = 0 \cr
  \dfrac{dI}{dx} + YV = 0
\end{cases}\implies\begin{cases}
  \dfrac{d^2V}{dx^2} = ZYV \cr
  \dfrac{d^2I}{dx^2} = ZYI
\end{cases}
$$

が得られるので、 **伝搬定数** $\gamma$ を

$$
\gamma = \sqrt{ZY} = \sqrt{R + j\omega L}\sqrt{G + j\omega C}
$$

と定義すれば一般解 $V(x)$ は

$$
V(x) = A\exp(-\gamma x) + B\exp(\gamma x) = V_i(x) + V_r(x)
$$

とおける。また **特性インピーダンス** $Z_0$ を

$$
Z_0 = \sqrt{\frac{Z}{Y}} = \frac{\sqrt{R + j\omega L}}{\sqrt{G + j\omega C}}
$$

と定義すれば一般解 $I(x)$ は

$$
Z_0I(x) = A\exp(-\gamma x) - B\exp(\gamma x) = Z_0I_i(x) - Z_0I_r(x)
$$

とおける。

::: page
:::

## 2 ポートとしての分布定数回路

![分布定数回路](img/2cables.zl.svg)

$$
\begin{cases}
  a(x) \triangleq \sqrt{V_i(x)I_i(x)} = Z_0^{-1/2}A\exp(-\gamma x) = \dfrac{Z_0^{-1/2}V(x) + Z_0^{1/2}I(x)}{2} \cr
  b(x) \triangleq \sqrt{V_r(x)I_r(x)} = Z_0^{-1/2}B\exp(\gamma x) = \dfrac{Z_0^{-1/2}V(x) - Z_0^{1/2}I(x)}{2}
\end{cases}
$$

とおけば、ある地点 $x = x$ におけるインピーダンス $Z(x)$ は

$$
Z(x) = \frac{V(x)}{I(x)} = \frac{Z_0^{1/2}a(x) + Z_0^{1/2}b(x)}{Z_0^{-1}\Big[Z_0^{1/2}a(x) - Z_0^{1/2}b(x)\Big]} = Z_0\frac{a(x) + b(x)}{a(x) - b(x)}
$$

と表せる。またこれらは $x = l$ における $V(l),I(l)$ を用いて

$$
\begin{cases}
  a(x) = Z_0^{-1/2}A\exp\Big[-\gamma l + \gamma(l - x)\Big] = \dfrac{Z_0^{-1/2}V(l) + Z_0^{1/2}I(l)}{2}\exp\gamma(l - x) \cr
  b(x) = Z_0^{-1/2}B\exp\Big[\gamma l - \gamma(l - x)\Big] = \dfrac{Z_0^{-1/2}V(l) - Z_0^{1/2}I(l)}{2}\exp\Big[-\gamma(l - x)\Big]
\end{cases}
$$

と表せるので

$$
\begin{cases}
  a(x) + b(x) = Z_0^{-1/2}Z_LI(l)\cosh\gamma(l - x) + Z_0^{1/2}I(l)\sinh\gamma(l - x) \cr
  a(x) - b(x) = Z_0^{-1/2}Z_LI(l)\sinh\gamma(l - x) + Z_0^{1/2}I(l)\cosh\gamma(l - x)
\end{cases}
$$

に注意して

$$
Z(x) = Z_0\frac{Z_L\cosh\gamma(l - x) + Z_0\sinh\gamma(l - x)}{Z_L\sinh\gamma(l - x) + Z_0\cosh\gamma(l - x)}
$$

と導けて、とくにインピーダンス整合 $Z_0 = Z_L$ のとき

$$
b(x) = \frac{[a(x) + b(x)] - [a(x) - b(x)]}{2} \equiv 0,\quad Z(x) = Z_0\frac{Z_0\exp\gamma(l - x)}{Z_0\exp\gamma(l - x)} \equiv Z_0
$$

がいえる。

::: page
:::

## $K$ 行列による表現

$$
\begin{cases}
  a(0) + b(0) = Z_0^{-1/2}V(0) = Z_0^{-1/2}V(l)\cosh(\gamma l) + Z_0^{1/2}I(l)\sinh(\gamma l) \cr
  a(0) - b(0) = Z_0^{1/2}I(0) = Z_0^{-1/2}V(l)\sinh(\gamma l) + Z_0^{1/2}I(l)\cosh(\gamma l)
\end{cases}
$$

すなわち

$$
\begin{pmatrix}
  V(0) \cr I(0)
\end{pmatrix} = \begin{pmatrix}
  \cosh(\gamma l) & Z_0\sinh(\gamma l) \cr
  Z_0^{-1}\sinh(\gamma l) & \cosh(\gamma l)
\end{pmatrix}\begin{pmatrix}
  V(l) \cr I(l)
\end{pmatrix}
$$

## $S$ 行列

| $S$   | $a_1(Z_2 = Z_0)$                                      | $a_2(Z_1 = Z_0)$                                      |
| ----- | ----------------------------------------------------- | ----------------------------------------------------- |
| $b_1$ | $s_{11} = \left.\dfrac{b_1}{a_1}\right\|_{Z_2 = Z_0}$ | $s_{12} = \left.\dfrac{b_1}{a_2}\right\|_{Z_1 = Z_0}$ |
| $b_2$ | $s_{21} = \left.\dfrac{b_2}{a_1}\right\|_{Z_2 = Z_0}$ | $s_{22} = \left.\dfrac{b_2}{a_2}\right\|_{Z_1 = Z_0}$ |

## $S$ 行列による表現

$$
K = \begin{pmatrix}
  \tilde{A} & Z_0\tilde{B} \cr
  Z_0^{-1}\tilde{C} & \tilde{D}
\end{pmatrix}
$$

とおけば

$$
S = \frac{1}{\tilde{A} + \tilde{B} + \tilde{C} + \tilde{D}}\begin{pmatrix}
  \tilde{A} + \tilde{B} - \tilde{C} - \tilde{D} & 2(\tilde{A}\tilde{D} - \tilde{B}\tilde{C}) \cr
  2 & - \tilde{A} + \tilde{B} - \tilde{C} + \tilde{D}
\end{pmatrix}
$$
