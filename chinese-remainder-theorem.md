## 中国の剰余定理

RSA暗号を理解するためには、フェルマーの小定理を一般化したオイラーの定理を知っておく必要があります。そして、オイラーの定理を理解するためには、オイラーの $$\phi$$ 関数という関数を求められるようになる必要があって、これには中国の剰余定理が必要不可欠です。オイラーの定理への第一歩として、この節では中国の剰余定理を説明します。

**定理** $$m_1, m_2, \cdots , m_n$$ を互いに素な自然数として、 $$a_1, a_2, \cdots , a_n$$ を整数とする。連立合同式

$$
\begin{align}
x &= a_1 \pmod{m_1} \\\
x &= a_2 \pmod{m_2} \\\
  &\cdots \\\
x &= a_n \pmod{m_n}
\end{align}
$$

を満たす整数 $$x$$ が $$m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_n$$ を法として一意に存在する。

**証明** まずは, そのような $$x$$ の存在を示す.

$$m=m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_n, M_i=\frac{m}{m_i}$$ として,

$$m_1, m_2, \cdots ,m_n$$が互いに素であるのだから、$$M_i=m_1\cdot{}m_2\cdot{}\cdots{}m_{i-1}\cdot{}m_{i+1}\cdot{}\cdots{}\cdot{}m_n$$は$$m_i$$と互いに素なものを掛け合わせたものであって, やはり$$m_i$$と互いに素となるので,

$$
gcd(M_i, m_i) = 1
$$

となる. ベズーの補題により, うまく$$y_i, z_i$$を選ぶと,

$$
M_iy_i+m_iz_i=gcd(M_i,m_i)=1
$$

にできる. これを変形して,

$$
\begin{align}
&M_iy_i + m_iz_i = 1 \\\
\Leftrightarrow \ &M_iy_i = -m_iz_i + 1 \\\
\Leftrightarrow \ &M_iy_i \equiv 1 \pmod{m_i}
\end{align}
$$

この $$y_i$$ は後述する拡張ユークリッドのアルゴリズムよって, 効率よく求めることができる.

こうして, $$y_i, M_i$$ が求まったら,

$$
x \equiv \sum_{i \in \{1, 2, \cdots , n\}} a_iy_iM_i \pmod{m}
$$

とおく. これは与えられた連立合同式を満たす. というのも,

$$
M_iy_i =y_iM_i \equiv 1 \pmod{m_i}
$$

であったから,

$$
a_iy_iM_i \equiv a_i \pmod{m_i}
$$

であるが, $$j \ne i$$ であるような $$j$$ については,

$$
\begin{align}
M_j &= \frac{m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_n}{m_j} \\\
&=m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_{j-1}\cdot{}m_{j+1}\cdot{}\cdots{}\cdot{}m_i\cdot{}\cdots{}\cdot{}m_n \\\
&=m_i \cdot (m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_{j-1}\cdot{}m_{j+1}\cdot{}\cdots{}\cdot{}m_{i-1}\cdot{}m_{i+1}\cdot{}\cdots{}\cdot{}m_n) \\\
&\equiv{} 0 \pmod{m_i}
\end{align}
$$

より,

$$
a_jy_jM_j \equiv 0 \pmod{m_i}
$$

となる.

したがって, 任意の $$i \in \{1, 2, \cdots{} n\}$$ について,

$$
\begin{align}
x &\equiv \sum_k a_ky_kM_k = a_iy_iM_i + \sum_{j (\ne i)} a_jy_jM_j \\\
  &\equiv a_iy_iM_i \pmod{m_i} \\\
\therefore x &\equiv a_i \pmod{m_i}
\end{align}
$$

となり, 確かに連立合同式を満たす.

以上より, $$x$$ が存在することが示された.

次に, 解が一意であることを示す.

連立合同式の任意の解を $$y$$ とおく. \($$x = y$$かもしれないし,そうでないかもしれない. 選び方は任意.\) すると, 任意の $$i \in \{1, 2, \cdots ,n\}$$ について

$$
y \equiv a_i \pmod{m_i}
$$

なのだから,

$$
x - y \equiv a_i - a_i \equiv 0 \pmod{m_i}
$$

である. $$m_1, m_2, \cdots , m_n$$ は互い
素なのだから, これらの全てで$$x-y$$ が割り切れるということは, $$x-y$$ が $$m_1\cdot{}m_2\cdot{}\cdots{}\cdot{}m_n$$ で割り切れることを意味する. \(わかりにくければ, $$n=2$$くらいの小さなケースで考えてみるとよい. たとえば, $$4, 9$$は互いに素であり, $$4$$でも$$9$$でも割り切れる数は$$4\cdot 9=36$$ で割り切れるずである.\)

したがって,

$$
x - y \equiv 0 \pmod{m}
$$

すなわち,

$$
x \equiv y \equiv \sum_{i \in \{1, 2, \cdots , n\}} a_iy_iM_i \pmod{m}
$$

であり, 解の一意性が示された ■