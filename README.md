# 回路理論 Ⅱ

## 分圧と分流

- 直列接続では $I$ が等しいため $V_i = Z_iI$ より各抵抗のインピーダンス $Z_i$ 比で電圧が分圧される。
- 並列接続では $V$ が等しいため $I_i = Y_iV$ より各抵抗のアドミタンス $Y_i$ 比で電流が分流される。

## 行列

| 行列 | 定義                                                                                | $Z$ 行列との変換                                                         | 相反条件           | 等価回路                                 |
| ---- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ------------------ | ---------------------------------------- |
| $Z$  | $\begin{pmatrix}V_1\cr V_2\end{pmatrix} = Z\begin{pmatrix}I_1\cr I_2\end{pmatrix}$  |                                                                          | $z_{12} = z_{21}$  | ![Z行列の等価回路](sec1/img/z.equiv.svg) |
| $Y$  | $\begin{pmatrix}I_1\cr I_2\end{pmatrix} = Y\begin{pmatrix}V_1\cr V_2\end{pmatrix}$  | $\|Z\|^{-1}\begin{pmatrix}z_{22}&-z_{12}\cr -z_{21}&z_{11}\end{pmatrix}$ | $y_{12} = y_{21}$  | ![Y行列の等価回路](sec1/img/y.equiv.svg) |
| $K$  | $\begin{pmatrix}V_1\cr I_1\end{pmatrix} = K\begin{pmatrix}V_2\cr -I_2\end{pmatrix}$ | $z_{21}^{-1}\begin{pmatrix}z_{11}&\|Z\|\cr 1&z_{22}\end{pmatrix}$        | $\|K\| = 1$        | ![K行列の等価回路](sec1/img/k.equiv.svg) |
| $H$  | $\begin{pmatrix}V_1\cr I_2\end{pmatrix} = H\begin{pmatrix}I_1\cr V_2\end{pmatrix}$  | $z_{22}^{-1}\begin{pmatrix}\|Z\|&z_{12}\cr -z_{21}&1\end{pmatrix}$       | $h_{12} = -h_{21}$ | ![H行列の等価回路](sec1/img/h.equiv.svg) |

::: page
:::

## 各成分の名称一覧

| $Z$   | 出力端開放 $I_1 (I_2 = 0)$                                               | 入力端開放 $I_2 (I_1 = 0)$                                               |
| ----- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| $V_1$ | 駆動点インピーダンス $z_{11} = \left.\dfrac{V_1}{I_1}\right\|_{I_2 = 0}$ | 伝達インピーダンス $z_{12} = \left.\dfrac{V_1}{I_2}\right\|_{I_1 = 0}$   |
| $V_2$ | 伝達インピーダンス $z_{21} = \left.\dfrac{V_2}{I_1}\right\|_{I_2 = 0}$   | 駆動点インピーダンス $z_{22} = \left.\dfrac{V_2}{I_2}\right\|_{I_1 = 0}$ |

| $Y$   | 出力端短絡 $V_1 (V_2 = 0)$                                             | 入力端短絡 $V_2 (V_1 = 0)$                                             |
| ----- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| $I_1$ | 駆動点アドミタンス $y_{11} = \left.\dfrac{I_1}{V_1}\right\|_{V_2 = 0}$ | 伝達アドミタンス $y_{12} = \left.\dfrac{I_1}{V_2}\right\|_{V_1 = 0}$   |
| $I_2$ | 伝達アドミタンス $y_{21} = \left.\dfrac{I_2}{V_1}\right\|_{V_2 = 0}$   | 駆動点アドミタンス $y_{22} = \left.\dfrac{I_2}{V_2}\right\|_{V_1 = 0}$ |

| $K$   | 出力端開放 $V_2 (I_2 = 0)$                                      | 出力端短絡 $-I_2 (V_2 = 0)$                                        |
| ----- | --------------------------------------------------------------- | ------------------------------------------------------------------ |
| $V_1$ | 電圧帰還率 $A = \left.\dfrac{V_1}{V_2}\right\|_{I_2 = 0}$       | 伝達インピーダンス $B = \left.\dfrac{V_1}{-I_2}\right\|_{V_2 = 0}$ |
| $I_1$ | 伝達アドミタンス $C = \left.\dfrac{I_1}{V_2}\right\|_{I_2 = 0}$ | 電流帰還率 $D = \left.\dfrac{I_1}{-I_2}\right\|_{V_2 = 0}$         |

| $H$   | 出力端短絡 $I_1 (V_2 = 0)$                                            | 入力端開放 $V_2 (I_1 = 0)$                                          |
| ----- | --------------------------------------------------------------------- | ------------------------------------------------------------------- |
| $V_1$ | 駆動点インピーダンス $h_i = \left.\dfrac{V_1}{I_1}\right\|_{V_2 = 0}$ | 電圧帰還率 $h_r = \left.\dfrac{V_1}{V_2}\right\|_{I_1 = 0}$         |
| $I_2$ | 電流増幅率 $h_f = \left.\dfrac{I_2}{I_1}\right\|_{V_2 = 0}$           | 駆動点アドミタンス $h_o = \left.\dfrac{I_2}{V_2}\right\|_{I_1 = 0}$ |

## 格子回路

![格子回路の回路図](sec1/img/grid.z.svg)

$$
Z = \frac{1}{\sum Z}
\begin{pmatrix}
  (Z_1 + Z_3)(Z_2 + Z_4) & Z_2Z_3 - Z_1Z_4 \cr
  Z_2Z_3 - Z_1Z_4 & (Z_1 + Z_2)(Z_3 + Z_4)
\end{pmatrix}
$$

$$
Y = \frac{1}{\sum Y}
\begin{pmatrix}
  (Y_1 + Y_2)(Y_3 + Y_4) & Y_2Y_3 - Y_1Y_4 \cr
  Y_2Y_3 - Y_1Y_4 & (Y_1 + Y_3)(Y_2 + Y_4)
\end{pmatrix}
$$

::: page
:::

## 理想変成器

$$
\dfrac{V_2}{V_1} = \dfrac{I_1}{-I_2} = n = \dfrac{n_2}{n_1} \cdot \mathrm{sgn} M
$$

## $Y - \Delta$ 変換表

|           | $Y \to \Delta$                                     | $\Delta \to Y$                                                     |
| --------- | -------------------------------------------------- | ------------------------------------------------------------------ |
| $Z \to Z$ | $Z_{ij} = \dfrac{Z_iZ_j + Z_jZ_k + Z_kZ_i}{Z_{k}}$ | $Z_k = \dfrac{Z_iZ_j}{Z_{ij} + Z_{jk} + Z_{ki}}$                   |
| $Z \to Y$ | $Y_{ij} = \dfrac{Z_{k}}{Z_iZ_j + Z_jZ_k + Z_kZ_i}$ | $Y_k = \dfrac{Z_{ij} + Z_{jk} + Z_{ki}}{Z_iZ_j}$                   |
| $Y \to Z$ | $Z_{ij} = \dfrac{Y_i + Y_j + Y_k}{Y_iY_j}$         | $Z_k = \dfrac{Y_{ij}}{Y_{ij}Y_{jk} + Y_{jk}Y_{ki} + Y_{ki}Y_{ij}}$ |
| $Y \to Y$ | $Y_{ij} = \dfrac{Y_iY_j}{Y_i + Y_j + Y_k}$         | $Y_k = \dfrac{Y_{ij}Y_{jk} + Y_{jk}Y_{ki} + Y_{ki}Y_{ij}}{Y_{ij}}$ |

## テブナンの定理

- $Z_{in} = Z_{out}' = \langle Z + Z_L \rangle = z_{11} - \dfrac{z_{12} z_{21}}{z_{22} + Z_L} = \dfrac{AZ_L + B}{CZ_L + D}$
- $Z_{out} = \langle Z + Z_G \rangle = z_{22} - \dfrac{z_{12} z_{21}}{z_{11} + Z_G}  = \dfrac{DZ_G + B}{CZ_G + A}$
- $V_{open} = \dfrac{z_{21}}{z_{11} + Z_G} E  = \dfrac{1}{CZ_G + A}E$

これより等価回路は次のように書ける。

![Z行列とテブナンの等価回路](sec2/img/zgl.equiv.svg)

## 供給電力最大の法則

$$
P = \frac{R |E|^2}{(R + R_0)^2 + (X + X_0)^2} \stackrel{Z = Z_0^\ast}{\leq} \frac{|E|^2}{4R_0}
$$

$Z = \overline{Z_0}$ のときに $P$ は最大値 $\dfrac{|E|^2}{4 \mathrm{Re}\left[Z\right]}$ をとる。

::: page
:::

## 電力利得

![Z行列とテブナンの等価回路](sec2/img/zgl.equiv.svg)

$Z_{in} \neq \overline{Z_G} , Z_L \neq \overline{Z_{out}}$ であるときの消費電力を「**動作電力利得**」という。

$$
G_p = \frac{P_L}{P_{in}} = \frac{\mathrm{Re}\left[Z_L\right]}{\mathrm{Re}\left[Z_{in}\right]}\frac{|Z_{in} + Z_G|^2}{|Z_L + Z_{out}|^2}\frac{|V_{open}|^2}{|E|^2}
$$

$Z_{in} = \overline{Z_G} , Z_L \neq \overline{Z_{out}}$ であるときの消費電力を「**変換電力利得**」という。

$$
G_t = \frac{P_L}{\mathrm{Max}\left[P_{in}\right]} = \frac{4\mathrm{Re}\left[Z_L\right]\mathrm{Re}\left[Z_G\right]}{|Z_L + Z_{out}|^2}\frac{|V_{open}|^2}{|E|^2}
$$

$Z_{in} = \overline{Z_G} , Z_L = \overline{Z_{out}}$ であるときの消費電力を「**有能電力利得**」という。

$$
G_a = \frac{\mathrm{Max}\left[P_L\right]}{\mathrm{Max}\left[P_{in}\right]} = \frac{\mathrm{Re}\left[Z_G\right]}{\mathrm{Re}\left[Z_L\right]}\frac{|V_{open}|^2}{|E|^2}
$$

## 分布定数回路

**伝搬定数** $\gamma$ と **特性インピーダンス** $Z_0$

$$
\gamma = \sqrt{ZY} = \sqrt{R + j\omega L}\sqrt{G + j\omega C} , \quad
Z_0 = \sqrt{\frac{Z}{Y}} = \frac{\sqrt{R + j\omega L}}{\sqrt{G + j\omega C}}
$$

入射波と反射波の関係

$$
\begin{cases}
  V(x) = A\exp(-\gamma x) + B\exp(\gamma x) = V_i(x) + V_r(x) \cr
  Z_0I(x) = A\exp(-\gamma x) - B\exp(\gamma x) = Z_0I_i(x) - Z_0I_r(x)
\end{cases}
$$

$$
\begin{cases}
  a(x) \triangleq \sqrt{V_i(x)I_i(x)} = Z_0^{-1/2}A\exp(-\gamma x) = \dfrac{Z_0^{-1/2}V(x) + Z_0^{1/2}I(x)}{2} \cr
  b(x) \triangleq \sqrt{V_r(x)I_r(x)} = Z_0^{-1/2}B\exp(\gamma x) = \dfrac{Z_0^{-1/2}V(x) - Z_0^{1/2}I(x)}{2}
\end{cases}
$$

$K$ 行列

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

::: page
:::

## キルヒホッフ則

### KCL - 第一法則

任意の節点に対する流入電流の並列積算は $0$ である。

$$
\sum_iI_i = 0
$$

### KVL - 第二法則

任意の閉路に沿った電圧の直列積算は $0$ である。

$$
\sum_iV_i = 0
$$

## 基本タイセット/カットセット行列

**補木枝** $c_1,\dots,c_m$ と **木枝** $t_1,\dots,t_n$

$$
  B_f = (I_m\mid B_p) = \left( \small
  \begin{array}{c:ccc|ccc}
    & c_{1} & \cdots & c_{m} & t_{1} & \cdots & t_{n} \cr \hdashline
    \mathcal{L}_{1} & 1 & & 0 & b_{11} & \cdots & b_{1n} \cr
    \vdots & & \ddots & & \vdots & \ddots & \vdots \cr
    \mathcal{L}_{m} & 0 & & 1 & b_{m1} & \ldots & b_{mn}
  \end{array}
  \right)
$$

$$
  C_f = (C_p\mid I_n) = \left( \small
  \begin{array}{c:ccc|ccc}
    & c_{1} & \cdots & c_{m} & t_{1} & \cdots & t_{n} \cr \hdashline
    \mathcal{C}_{1} & c_{11} & \cdots & c_{1m} & 1 & & 0 \cr
    \vdots & \vdots & \ddots & \vdots & & \ddots &\cr
    \mathcal{C}_{n} & c_{n1} & \ldots & c_{nm} & 0 & & 1
  \end{array}
  \right)
$$

## 閉路電流法

1. 枝電流を基本タイセットによる閉路電流で表現する、つまり基本タイセット行列 $B_f$ を求める
2. 電流 $I_\mathcal{L}$ により電圧 $V = ZI - E = Z(B_f^\text{T}I_\mathcal{L}) - E$ を表現する
3. KVL : $B_fV = \mathbf0$ を適用して $I_\mathcal{L}$ を求める
