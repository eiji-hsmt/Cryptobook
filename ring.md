### 環

整数$$\mathbb{Z}$$の掛け算を思い浮かべてみる. 掛け算の定まった整数には, どのような性質が見られるだろうか.

まず, 任意に選んだ$$a, b, c \in \mathbb{Z}$$に対して,


$$
a \cdot (b \cdot c) = (a \cdot b) \cdot c
$$


を満たす. すなわち, 結合的である. たとえば,


$$
\begin{align}
3 \cdot (4 \cdot 5) &= 60 \\\
(3 \cdot 4) \cdot 5 &= 60 \\\
であり,\hspace{16pt} 3 \cdot (4 \cdot 5) &= (3 \cdot 4) \cdot 5
\end{align}
$$


である. $$3, 4, 5$$ に限らず全ての整数についてこれが成り立つ. 整数の掛け算はどの順序で計算しても同じ結果となるのだ.

この他, $$1 \in \mathbb{Z}$$ が存在して \(※ただの$$1$$です. $$1 + 1 = 2$$の$$1$$ね.\) 任意の$$x \in \mathbb{Z}$$にについて,


$$
x \cdot 1 = 1 \cdot x = x
$$


となる. すなわち, 乗法の単位元が存在する.

しかしながら, $$0 \cdot a = 1$$となる$$a$$は存在しないため, 必ずしも逆元は存在しない. \(少なくとも$$0$$の逆元, つまり逆数は存在しない.\)

以上のことから, 整数$$\mathbb{Z}$$の掛け算は, モノイドをなすことがわかる.

さらに,


$$
(x + y) \cdot s = x \cdot s + y \cdot s \\\
s \cdot (x + y) = s \cdot x + s \cdot y
$$


という性質も満たす. これを分配律 \(分配法則\) という.

たとえば, $$(10 + 2) \cdot 3$$ を


$$
(10 + 2) \cdot 3 = 12 \cdot 3 = 36
$$


のように計算しても, あるいは分配法則を利用して


$$
(10 + 2) \cdot 3 = 10 \cdot 3 + 2 \cdot 3 = 30 + 6 = 36
$$


のように計算してもよいことを, わたしたちは知っている.

整数の足し算と掛け算とを考えると, 足し算については可換群に, 掛け算についてはモノイドになっており, 分配律が成り立っていることがわかる. このような代数的構造を環という.

#### 例

整数 $$\mathbb{Z}$$ を同値関係 $$\equiv \pmod{n}$$ によって類別して得られた同値類に整数 $$\mathbb{Z}$$ 同様に加法を定めると可換群になるのであった. この類に次のように乗法を定めることによって, 乗法についてはモノイドをなし, また分配律 \(分配法則\) が成立するため, 環をなす.

$$n$$ で割って $$m$$ 余る数を $$[m]$$ と表すことにして,


$$
\begin{align}

[l] \cdot ([s] \cdot [t]) &= (kn + l) \cdot ((k^\prime n + s) \cdot (k^{\prime \prime } n + t)) \\\
                          &= (kn + l) \cdot (k^\prime n + s) \cdot (k^{\prime \prime } n + t) \\\
                          &= ((kn + l) \cdot (k^\prime n + s)) \cdot (k^{\prime \prime } n + t) \\\
                          &\equiv ([l] \cdot [s]) \cdot [t] \pmod{n}
\end{align}
$$


より, 乗法に関する結合律が成立,


$$
\begin{align}
[m][1] &= (kn + m) \cdot (k^\prime n + 1) \\\
       &= (kk^\prime n + k + k^\prime m)\cdot n + m \cdot 1 \\\
       &\equiv m \pmod{n} \\\
       &\equiv [m] \pmod{n} \\\
\end{align}
$$


より, 乗法に関する単位元 $$[1]$$ が存在し,


$$
\begin{align}
[l] \cdot ([s] + [t]) &= (kn + l) \cdot ((k^\prime n + s) + (k^{\prime \prime } n + t)) \\\

                              &= n \cdot (\cdots ) + l \cdot ((k^\prime n +s) + (k^{\prime \prime } n + t)) \\\

                              &\equiv l \cdot (((k^\prime n +s) + (k^{\prime \prime } n + t)) \pmod{n} \\\

                              &= l \cdot (k^\prime n + s) + l \cdot (k^{\prime \prime} n + t) \\\

                              &= (l k^\prime + l k^{\prime \prime } ) n + l \cdot s + l \cdot t \\\

                              &\equiv l \cdot s + l \cdot t \pmod{n} \\\
                              &\equiv [l] \cdot [s] + [l] \cdot [t] \pmod{n} \\\
\\\

([s] + [t]) \cdot [l] &= ((k^\prime n + s) + (k^{\prime \prime } n + t)) \cdot (kn + l) \\\

                              &= (\cdots ) \cdot kn + ((k^\prime n +s) + (k^{\prime \prime } n + t)) \cdot l \\\

                              &\equiv (((k^\prime n +s) + (k^{\prime \prime } n + t)) \cdot l \pmod{n} \\\

                              &= (k^\prime n + s) \cdot l + (k^{\prime \prime} n + t) \cdot l \\\

                              &= (k^\prime l + k^{\prime \prime } l) n + s \cdot l + t \cdot l \\\

                              &\equiv s \cdot l + t \cdot l \pmod{n} \\\
                              &\equiv [s] \cdot [l] + [t] \cdot [l] \pmod{n}

\end{align}
$$


から, 乗法と加法について分配律が成立している. よって, これは環である.



この環を剰余環 $$\mathbb{Z}/n\mathbb{Z}$$ といって, 暗号理論, 暗号技術のいたるところに顔を出す.

