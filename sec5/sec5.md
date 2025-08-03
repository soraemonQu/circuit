# 5. グラフ理論

第十一回～第十ニ回の内容。

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

## 回路の記述

- 補木枝 $c_1,\dots,c_m$
- 木枝 $t_1,\dots,t_n$
- 電流ベクトル $I = (I_{c_{1}}\ \cdots\  I_{c_{m}}\  I_{t_{1}}\ \cdots\  I_{t_{n}})^\text{T}$
- 閉路電流 $I_\mathcal{L} = (I_{\mathcal{L}_{1}}\ \cdots\  I_{\mathcal{L}_{m}})^\text{T} = (I_{c_{1}}\ \cdots\  I_{c_{m}})^\text{T}$
- 電圧ベクトル $V = (V_{c_{1}}\ \cdots\  V_{c_{m}}\  V_{t_{1}}\ \cdots\  V_{t_{n}})^\text{T}$
- 木枝電圧 $V_\mathcal{C} = (V_{\mathcal{C}_{1}}\ \cdots\  V_{\mathcal{C}_{n}})^\text{T} = (V_{t_{1}}\ \cdots\  V_{t_{n}})^\text{T}$
- 基本タイセット $\mathcal{L}_{1},\dots,\mathcal{L}_{m}$
- 基本カットセット $\mathcal{C}_{1},\dots,\mathcal{C}_{n}$
- 基本タイセット行列 $B_f$ : $I = B_f^\text{T} I_{\mathcal{L}}$ を満たす行列
- 基本カットセット行列 $C_f$ : $V = C_f^\text{T} V_{\mathcal{C}}$ を満たす行列

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

::: page
:::

## KCL と KVL の行列表現

### KCL

$$
\begin{pmatrix}
  \sum_ic_{1i}I_{i} \cr
  \vdots \cr
  \sum_ic_{ni}I_{i}
\end{pmatrix} = \mathbf0 \implies C_fI = \mathbf0
$$

### KVL

$$
\begin{pmatrix}
  \sum_ib_{1i}V_{i} \cr
  \vdots \cr
  \sum_ib_{mi}V_{i}
\end{pmatrix} = \mathbf0 \implies B_fV = \mathbf0
$$

## 回路方程式の解法

$$
A\boldsymbol{x} = \mathbf0 \implies \det A = 0
$$

### 閉路電流法

1. 枝電流を基本タイセットによる閉路電流で表現する、つまり基本タイセット行列 $B_f$ を求める
2. 電流 $I_\mathcal{L}$ により電圧 $V = ZI - E = Z(B_f^\text{T}I_\mathcal{L}) - E$ を表現する
3. KVL : $B_fV = \mathbf0$ を適用して $I_\mathcal{L}$ を求める

### 節点電位法

節点電位とは名ばかりで実際には木枝電圧を使うことで自由度を $1$ 削減することが多い。

1. 枝電圧を基本カットセットによる木枝電圧で表現する、つまり基本カットセット行列 $C_f$ を求める
2. 電圧 $V_\mathcal{C}$ により電流 $I = YV + J = Y(C_f^\text{T}V_\mathcal{C}) + J$ を表現する
3. KCL : $C_fI = \mathbf0$ を適用して $V_\mathcal{C}$ を求める

### 枝電流法

1. 基本セット行列 $b_f$ および $C_f$ を求める
2. 電流 $I$ により電圧 $V = ZI - E$ を表現する
3. KCL : $B_fV = B_f(ZI - E) = \mathbf0$ および KVL : $C_fI = \mathbf0$ を適用して $I$ を求める
