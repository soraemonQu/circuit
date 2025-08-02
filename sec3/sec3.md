# 3. 動作減衰量

第七回～第九回の内容。

## 伝送量

電流の **伝送量** $\theta_I$ を以下で定義する

$$
\theta_I = \ln\frac{I_1}{-I_2}
$$

電圧の **伝送量** $\theta_V$ と **振幅減衰量** $\tilde\alpha = \mathrm{Re}\left[\theta_V\right]$ および **位相量** $\tilde\beta = \mathrm{Im}\left[\theta_V\right]$ を以下で定義する

$$
\theta_V = \ln\frac{V_1}{V_2} = \ln\left|\frac{V_1}{V_2}\right| + j\arg\frac{V_1}{V_2} = \tilde\alpha + j\tilde\beta
$$

## 動作減衰量

振幅減衰量 $\tilde\alpha$ は以下のようにデシベル表記できる

$$
\tilde\alpha' = 20\log_{10}\left|\frac{V_1}{V_2}\right|\quad\mathrm{[dB]}
$$

ただし底の変換公式より変換式は以下のようになる

$$
\tilde\alpha' = (20\log_{10}e)\tilde\alpha \approx 8.6859\tilde\alpha\quad\mathrm{[dB]}
$$

ここで $V_1 \leq E/2$ $^{[要出典]}$ であるから、以下の $\alpha$ を **動作減衰量** という

$$
\alpha = 20\log_{10}\left|\frac{E/2}{V_2}\right|\quad\mathrm{[dB]}
$$

また **電流比** は

$$
20\log_{10}\left|\frac{I_1}{-I_2}\right|\quad\mathrm{[dB]}
$$

**電力の損失比** は

$$
20\log_{10}\sqrt{\frac{P_1}{P_2}} = 10\log_{10}\frac{P_1}{P_2}\quad\mathrm{[dB]}
$$

::: page
:::

### $K$行列における動作減衰量

次の回路を考える。

![K行列回路](img/k.alpha.svg)

テブナンの等価回路を用いると以下のように書ける。

$$
V_2 = \frac{Z_LV_{open}}{Z_L + Z_{out}} = \frac{Z_L\cdot\dfrac{E}{CZ_G + A}}{Z_L + \dfrac{DZ_G + B}{CZ_G + A}} = \frac{Z_LE}{(CZ_G + A)Z_L + (DZ_G + B)}
$$

ここで

$$
Z_G = Z_L = Z_0,\qquad K = \begin{pmatrix}
  1 - XB & jX \cr
  jB & 1
\end{pmatrix}
$$

を代入して

$$
\frac{E}{2V_2} = \frac{(jBZ_0 + 1 - XB)Z_0 + Z_0 + jX}{2Z_0} = \left(1 - \frac{XB}{2}\right) + j\left(\frac{X}{2Z_0} + \frac{BZ_0}{2}\right)
$$

となるから

$$
\left|\frac{E}{2V_2}\right| = \sqrt{\left(1 - \frac{XB}{2}\right)^2 + \left(\frac{X}{2Z_0} + \frac{BZ_0}{2}\right)^2}
$$

これより動作減衰量 $\alpha_{X,B}$ は次のようになる。

$$
\alpha_{X,B} = 20\log_{10}\sqrt{\left(1 - \frac{XB}{2}\right)^2 + \left(\frac{X}{2Z_0} + \frac{BZ_0}{2}\right)^2} \mathrm{[dB]}
$$

とくに $B = 0\mho$ の回路 $N_X$ における動作減衰量 $\alpha_X$ は

$$
\alpha_X = 20\log_{10}\sqrt{1 + \left(\frac{X}{2Z_0}\right)^2} \mathrm{[dB]}
$$

あるいは $X = 0\Omega$ の回路 $N_B$ における動作減衰量 $\alpha_B$ は

$$
\alpha_B = 20\log_{10}\sqrt{1 + \left(\frac{BZ_0}{2}\right)^2} \mathrm{[dB]}
$$

::: page
:::

## Filter

**フィルター (Filter)** とは、ある領域の角周波数を遮断するような、つまり **周波数により動作減衰量を調整する** ような 2 ポート素子のことである。

ここで遮断角周波数 $\omega_c$ における動作減衰量 $\alpha_c$ は以下の通りとなる。

$$
\alpha_c = 20\log_{10}\sqrt{2}\mathrm{dB} = 10\log_{10}2\mathrm{dB} \approx 3.0103\mathrm{dB}
$$

### Low Pass Filter (LPF)

低周域 $[0,\omega_c]$ の動作減衰量を小さくする。

|                       | $0 \leq \omega \leq \omega_c$ | $\omega_c < \omega$   |
| --------------------- | ----------------------------- | --------------------- |
| 動作減衰量 $\alpha_l$ | $\alpha_l \leq \alpha_c$      | $\alpha_l > \alpha_c$ |
| 領域                  | 通過域                        | 減衰域                |

$$
\alpha_l = 20\log_{10}\sqrt{1 + \left(\frac{\omega}{\omega_c}\right)^2}\quad\mathrm{[dB]}
$$

#### LPF の $N_X$ による実装

$\alpha_X$ と比較すれば $\dfrac{X}{2Z_0} = \pm\dfrac{\omega}{\omega_c}$ となるため、仮に $jX \equiv j\omega L$ とすれば、遮断角周波数は

$$
\omega_c = 2\cdot\dfrac{Z_0}{L}
$$

#### LPF の $N_B$ による実装

$\alpha_B$ と比較すれば $\dfrac{BZ_0}{2} = \pm\dfrac{\omega}{\omega_c}$ となるため、仮に $jB \equiv j\omega C$ とすれば、遮断角周波数は

$$
\omega_c = 2\cdot\dfrac{1}{CZ_0}
$$

::: page
:::

### High Pass Filter (HPF)

高周域 $[\omega_c,\infty)$ の動作減衰量を小さくする。

|                       | $0 \leq \omega < \omega_c$ | $\omega_c \leq \omega$   |
| --------------------- | -------------------------- | ------------------------ |
| 動作減衰量 $\alpha_h$ | $\alpha_h > \alpha_c$      | $\alpha_h \leq \alpha_c$ |
| 領域                  | 減衰域                     | 通過域                   |

$$
\alpha_h = 20\log_{10}\sqrt{1 + \left(\frac{\omega_c}{\omega}\right)^2}\quad\mathrm{[dB]}
$$

#### HPF の $N_X$ による実装

$\alpha_X$ と比較すれば $\dfrac{X}{2Z_0} = \pm\dfrac{\omega_c}{\omega}$ となるため、仮に $jX \equiv (j\omega C)^{-1}$ とすれば、遮断角周波数は

$$
\omega_h = \dfrac12\cdot\dfrac{1}{CZ_0}
$$

#### HPF の $N_B$ による実装

$\alpha_B$ と比較すれば $\dfrac{BZ_0}{2} = \pm\dfrac{\omega_c}{\omega}$ となるため、仮に $jB \equiv (j\omega L)^{-1}$ とすれば、遮断角周波数は

$$
\omega_h = \dfrac12\cdot\dfrac{Z_0}{L}
$$

#### LPF to HPF

$\alpha_l$ と $\alpha_h$ を比較すれば $\dfrac{\omega}{\omega_c} = \pm\dfrac{\omega_c'}{\omega'}$ となるため、負号を採用して両辺に $j\omega_c$ をかけて

$$
j\omega \xrightarrow{\rm LPF \to HPF} \frac{\omega_c\omega_c'}{j\omega}
$$

::: page
:::

### Band Pass Filter (BPF)

通過帯域 $[\omega_1, \omega_2]$ の動作減衰量を小さくする。

|                       | $0 \leq \omega < \omega_1$ | $\omega_1 \leq \omega \leq \omega_2$ | $\omega_2 < \omega$   |
| --------------------- | -------------------------- | ------------------------------------ | --------------------- |
| 動作減衰量 $\alpha_b$ | $\alpha_b > \alpha_c$      | $\alpha_b \leq \alpha_c$             | $\alpha_h > \alpha_c$ |
| 領域                  | 減衰域                     | 通過帯域                             | 減衰域                |

中心周波数 $\omega_0 \equiv \sqrt{\omega_1\omega_2}$ と比帯域 $w \equiv \dfrac{\omega_2 - \omega_1}{\omega_0}$ を用いて

$$
\alpha_b = 20\log_{10}\sqrt{1 + \frac{1}{w^2}\left(\frac{\omega}{\omega_0} - \frac{\omega_0}{\omega}\right)^2}\quad\mathrm{[dB]}
$$

#### BPF の $N_X$ による実装

$\alpha_X$ と比較すれば $\dfrac{X}{2Z_0} = \pm\dfrac1w\left(\dfrac{\omega}{\omega_0}-\dfrac{\omega_0}{\omega}\right)$ となるため、仮に $jX \equiv j\omega L + (j\omega C)^{-1}$ とすれば

$$
\frac{L}{2Z_0} = \frac{1}{w\omega_0},\qquad\frac{1}{2CZ_0} = \frac{\omega_0}{w}
$$

であるから、中心周波数と比帯域は

$$
\omega_0 = \frac{1}{\sqrt{LC}},\qquad w = 2Z_0\sqrt{\frac{C}{L}}
$$

#### BPF の $N_B$ による実装

$\alpha_B$ と比較すれば $\dfrac{BZ_0}{2} = \pm\dfrac1w\left(\dfrac{\omega}{\omega_0} - \dfrac{\omega_0}{\omega}\right)$ となるため、仮に $jB \equiv (j\omega L)^{-1} + j\omega C$ とすれば

$$
\frac{CZ_0}{2} = \frac{1}{w\omega_0},\qquad\frac{Z_0}{2L} = \frac{\omega_0}{w}
$$

であるから、中心周波数と比帯域は

$$
\omega_0 = \frac{1}{\sqrt{LC}},\qquad w = \frac{2}{Z_0}\sqrt{\frac{L}{C}}
$$

#### LPF to BPF

$\alpha_l$ と $\alpha_b$ を比較すれば $\dfrac{\omega}{\omega_c} = \pm\dfrac1w\left(\dfrac{\omega}{\omega_0} - \dfrac{\omega_0}{\omega}\right)$ となるため、正号を採用して両辺に $j\omega_c$ をかけて

$$
j\omega \xrightarrow{\rm LPF \to BPF} \frac{\omega_c}{w}\left(\frac{j\omega}{\omega_0} + \frac{\omega_0}{j\omega}\right)
$$

::: page
:::

## 能動ポート

### Bipolar Junction Transistor (BJT)

![BJTの回路記号](img/bjt.sym.svg)

Base、Emitter、Collector の三端子素子であり、それぞれに相当する抵抗 $r_B, r_E, r_C$ 等価回路を設計できる。

BJT の継続行列はエミッタ効率 $\alpha \lesssim 1$ および電流増幅率 $\beta = \dfrac{\alpha}{1 - \alpha} \gg 1$ により以下で表せる。

$$
H = \begin{pmatrix}
  r_B + \dfrac{r_Er_C(1 - \alpha)}{r_E + r_C(1 - \alpha)}(1 + \beta) & \dfrac{r_E}{r_C(1 - \alpha) + r_E} \cr
  \dfrac{\alpha r_C - r_E}{r_C(1 - \alpha) + r_E} & \dfrac{1}{r_C(1 - \alpha) + r_E}
\end{pmatrix}
$$

この BJT は以下を満たす。

- **非相反条件** $h_r + h_f \neq 0$
- **高利得性** $h_f \gg 1$
- **単方向性** $h_r = 0$

とくに $r_C(1 - \alpha) \gg r_E, r_B$ 条件下では

$$
H = \begin{pmatrix}
  h_{ie} & h_{re} \cr
  h_{fe} & h_{oe}
\end{pmatrix} = \begin{pmatrix}
  r_B + r_E(1 + \beta) & 0 \cr
  \beta & 0
\end{pmatrix}
$$

::: page
:::

### Field Effective Transistor (FET)

![FETの回路記号](img/fet.sym.svg)

Gate、Source、Drain の三端子素子であり、Gate $C_1$ Drain-Source $C_2$ Gate-Drain $C_3$ の各容量と、相互インダクタンス $g_m$ および出力抵抗 $R$ によりそのアドミタンス行列は以下で示される。

$$
Y = \begin{pmatrix}
  j\omega(C_1 + C_3) & -j\omega C_3 \cr
  g_m - j\omega C_3 & \dfrac1R + j\omega(C_2 + C_3)
\end{pmatrix}
$$

単方向性 $C_3 = 0$ を考慮すれば

$$
Y = \begin{pmatrix}
  j\omega C_1 & 0 \cr
  g_m & \dfrac1R + j\omega C_2
\end{pmatrix},\qquad H = \begin{pmatrix}
  (j\omega C_1)^{-1} & 0 \cr
  g_m(j\omega C_1)^{-1} & \dfrac1R + j\omega C_2
\end{pmatrix}
$$
