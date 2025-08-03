# 2. 回路定理

第四回～第六回の内容。

## 重ね合わせの理

各電源が与える影響は、それぞれを独立して観測したときの影響を重ね合わせたものである。

![N0N回路](img/supposn.svg)

電源回路 $N_0 = \{ E_1, \ldots, E_m, J_1, \ldots, J_n \}$ に抵抗 $N$ を接続したとき、 $N$ にかかる電圧と電流について

$$
V_{N_0} = \sum_{1 \leq i \leq m} V_{ \{ E_i \} } + \sum_{1 \leq j \leq n} V_{ \{ J_j \} }, \qquad I_{N_0} = \sum_{1 \leq i \leq m} I_{ \{ E_i \} } + \sum_{1 \leq j \leq n} I_{ \{ J_j \} }
$$

::: page
:::

## 補償定理

![補償定理](img/diff.svg)

電源回路で電流 $I$ が走る枝に $Z$ を挿入しても、これに代わる電圧源 $ZI$ を直列に挿入すれば等価である。

::: original
![Zの挿入](img/diff.inserted.svg)
:::

挿入した $ZI$ を取り除く手順は、これと並列に更なる電圧源 $-ZI$ を挿入することと等価である。

これは元と等価な回路と、電源を無効化の上で $-ZI$ を挿入した回路との重ね合わせで表される。

ゆえに $Z$ を挿入したことによる影響は、電源を無効化の上で $-ZI$ を挿入した回路の分と同じである。

::: page
:::

## 入力インピーダンス $Z_{in}$

![入力インピーダンス](img/zin.svg)

$Z$ と $Z_L$ の接続について

$$
V_2 = z_{21} I_1 + z_{22} I_2 = Z_L (-I_2) \implies I_2 = -\frac{z_{21}}{z_{22} + Z_L} I_1
$$

がいえるから入力インピーダンス $Z_{in} = \langle Z + Z_L \rangle$ は

$$
Z_{in} = \frac{V_1}{I_1} = \frac{z_{11} I_1 + z_{12} I_2}{I_1} = z_{11} - \frac{z_{12} z_{21}}{z_{22} + Z_L}
$$

であり、ここで $Z$ 行列と $K$ 行列の変換式

$$
\begin{pmatrix}
  z_{11} & z_{12} \cr
  z_{21} & z_{22}
\end{pmatrix} =
\frac{1}{C}\begin{pmatrix}
  A & AD - BC \cr
  1 & D
\end{pmatrix}
$$

を用いると以下の整った形となる。

$$
Z_{in} = \frac{A}{C} - \frac{AD - BC}{C(D + CZ_L)} = \frac{AD + ACZ_L - AD + BC}{C^2Z_L + CD} = \frac{AZ_L + B}{CZ_L + D}
$$

## 入力端開放電圧

![入力端開放電圧](img/vin.svg)

さらに抵抗 $Z_L$ と直列に電圧源 $E$ を接続した場合を考える。ただし入力電流は無視できるものとする。

$$
V_2 = z_{21} \cancel{I_1} + z_{22} I_2 = Z_L (-I_2) + E \implies I_2 = \frac{1}{z_{22} + Z_L} E
$$

となるから入力端開放電圧は次のようになる。

$$
V_1 = z_{11} \cancel{I_1} + z_{12} I_2 = \frac{z_{12}}{z_{22} + Z_L} E = \dfrac{AD - BC}{CZ_L + D} E
$$

::: page
:::

## 出力インピーダンス $Z_{out}$

![出力インピーダンス](img/zout.svg)

$Z$ と $Z_G$ の接続について

$$
V_1 = z_{11} I_1 + z_{12} I_2 = Z_G (-I_1) \implies I_1 = -\frac{z_{12}}{z_{11} + Z_G} I_2
$$

がいえるから出力インピーダンス $Z_{out} = \langle Z + Z_G \rangle$ は

$$
Z_{out} = \frac{V_2}{I_2} = \frac{z_{21} I_1 + z_{22} I_2}{I_2} = z_{22} - \frac{z_{12} z_{21}}{z_{11} + Z_G}
$$

であり、$K$ 行列を用いると以下の形で表される。

$$
Z_{out} = \frac{D}{C} - \frac{AD - BC}{C(A + CZ_G)} = \frac{AD + CDZ_G - AD + BC}{C^2Z_G + CA} = \frac{DZ_G + B}{CZ_G + A}
$$

## 出力端開放電圧 $V_{open}$

![出力端開放電圧](img/vout.svg)

さらに抵抗 $Z_G$ と直列に電圧源 $E$ を接続した場合を考える。ただし出力電流は無視できるものとする。

$$
V_1 = z_{11} I_1 + z_{12} \cancel{I_2} = Z_G (-I_1) + E \implies I_1 = \frac{1}{z_{11} + Z_G}E
$$

となるから出力端開放電圧は入力端開放電圧と比べても簡単な形となる。

$$
V_2 = z_{21} I_1 + z_{22} \cancel{I_2} = \frac{z_{21}}{z_{11} + Z_G}E = \frac{1}{CZ_G + A}E
$$

::: page
:::

## テブナンの定理

![テブナンの等価回路](img/thevenin.svg)

電源を含むどんな複雑な回路 $N_0$ も、内部インピーダンス $Z_{out}$ を直列接続した電流源 $V_{open}$ により等価表現できる。

- **出力インピーダンス** $Z_{out}$ : $N_0$ 内の電源をすべて無効化したときの $N_0$ のインピーダンス
- **出力開放電圧** $V_{open}$ : $N$ を **開放消去** したとき $N_0$ に生じる電圧

### 行列への適用

![Z行列の回路](img/zgl.svg)

上の $Z$ 行列を用いた回路の等価回路を考える。

ノートンの定理を適用してみる。具体値の計算は前節を参照。

1. $N \gets Z_G$ としたとき
   - $Z_{in} = Z_{out}' = \langle Z + Z_L \rangle = z_{11} - \dfrac{z_{12} z_{21}}{z_{22} + Z_L}$
   - $V_{open}' = E$ ($\because$ 断線により回路に電流は流れず抵抗で電源電圧が降下しないから)
2. $N \gets Z_L$ としたとき
   - $Z_{out} = \langle Z + Z_G \rangle = z_{22} - \dfrac{z_{12} z_{21}}{z_{11} + Z_G}$
   - $V_{open} = \dfrac{z_{21}}{z_{11} + Z_G} E$

これより等価回路は次のように書ける。

![Z行列とテブナンの等価回路](img/zgl.equiv.svg)

::: page
:::

## ノートンの定理

![ノートンの等価回路](img/norton.svg)

電源を含むどんな複雑な回路 $N_0$ も、内部アドミタンス $Y_{out}$ を並列接続した電圧源 $I_{close}$ により等価表現できる。

- **出力アドミタンス** $Y_{out}$ : $N_0$ 内の電源をすべて無効化したときの $N_0$ のアドミタンス
- **出力短絡電流** $I_{close}$ : $N$ を **短絡消去** したとき $N_0$ に生じる電流

## 供給電力最大の法則

内部インピーダンス $Z_0$ の電圧源 $E$ に接続したインピーダンス $Z$ の消費電力 $P$ を最大化したい。

回路を走る電流は

$$
I = \frac{E}{Z + Z_0}
$$

これより $P$ は

$$
P = \mathrm{Re}\left[V\overline{I}\right] = \mathrm{Re}\left[Z\right]|I|^2 = \frac{\mathrm{Re}\left[Z\right] |E|^2}{|Z + Z_0|^2}
$$

$Z = R + jX ; Z_0 = R_0 + jX_0 ; R, R_0 > 0$ と仮定すれば

$$
P = \frac{R |E|^2}{(R + R_0)^2 + (X + X_0)^2} \stackrel{X + X_0 = 0}{\leq} \frac{R |E|^2}{(R + R_0)^2} = \frac{|E|^2}{\left(R + \dfrac{R_0^2}{R}\right) + 2R_0} \stackrel{R = R_0}{\leq} \frac{|E|^2}{4R_0}
$$

これより $Z = \overline{Z_0}$ のときに $P$ は最大値 $\dfrac{|E|^2}{4 \mathrm{Re}\left[Z\right]}$ をとる。

また、 $Z = \overline{Z_0}$ であることを電力的に「**整合が取れている**」といい、このときの電力を「**有能電力**」という。

::: page
:::

## 電力利得

次の回路において、発電側回路の $Z_{in}$ で消費される電力 $P_{in}$ と供給側回路の $Z_L$ で消費される電力 $P_L$ に関する電力利得 $G = \dfrac{P_L}{Z_{in}}$ を考える。

![Z行列とテブナンの等価回路](img/zgl.equiv.svg)

### 整合が取れていないとき

$Z_{in} \neq \overline{Z_G} , Z_L \neq \overline{Z_{out}}$ であるときの消費電力を「**動作電力利得**」という。

$$
G_p = \frac{P_L}{P_{in}} = \left.\frac{\mathrm{Re}\left[Z_L\right] |V_{open}|^2}{|Z_L + Z_{out}|^2}\middle/\frac{\mathrm{Re}\left[Z_{in}\right] |E|^2}{|Z_{in} + Z_G|^2}\right. = \frac{\mathrm{Re}\left[Z_L\right]}{\mathrm{Re}\left[Z_{in}\right]}\frac{|Z_{in} + Z_G|^2}{|Z_L + Z_{out}|^2}\frac{|V_{open}|^2}{|E|^2}
$$

### 発電側の整合が取れているとき

$Z_{in} = \overline{Z_G} , Z_L \neq \overline{Z_{out}}$ であるときの消費電力を「**変換電力利得**」という。

$$
G_t = \frac{P_L}{\mathrm{Max}\left[P_{in}\right]} = \left.\frac{\mathrm{Re}\left[Z_L\right] |V_{open}|^2}{|Z_L + Z_{out}|^2}\middle/\frac{|E|^2}{4\mathrm{Re}\left[Z_{in}\right]}\right. = \frac{4\mathrm{Re}\left[Z_L\right]\mathrm{Re}\left[Z_G\right]}{|Z_L + Z_{out}|^2}\frac{|V_{open}|^2}{|E|^2}
$$

### 両側の整合が取れているとき

$Z_{in} = \overline{Z_G} , Z_L = \overline{Z_{out}}$ であるときの消費電力を「**有能電力利得**」という。

$$
G_a = \frac{\mathrm{Max}\left[P_L\right]}{\mathrm{Max}\left[P_{in}\right]} = \left.\frac{|V_{open}|^2}{4\mathrm{Re}\left[Z_L\right]}\middle/\frac{|E|^2}{4\mathrm{Re}\left[Z_{in}\right]}\right. = \frac{\mathrm{Re}\left[Z_G\right]}{\mathrm{Re}\left[Z_L\right]}\frac{|V_{open}|^2}{|E|^2}
$$
