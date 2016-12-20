### ベズーの補題

整数$$m, n$$に対して, $$m$$の倍数と$$n$$の倍数の足し算で表現できる全ての数の集合を $$m\mathbb{Z}+n\mathbb{Z}$$ と表す.

たとえば, $$4\mathbb{Z}+6\mathbb{Z}$$は,

$$
4\mathbb{Z}+6\mathbb{Z} = \{\cdots , -10, -8, -6, -4, -2, 0, 2, 4, 6, 8, 10, \cdots \}
$$

である. 実際, これらの数は下に示す通り, $$4$$の倍数と$$6$$の倍数の足し算で表現できる.

$$
\begin{align}
\cdots\\\
-10 &= 4 \cdot (-1) + 6 \cdot (-1) \\\
 -8 &= 4 \cdot (-2) + 6 \cdot 0 \\\
 -6 &= 4 \cdot 0    + 6 \cdot (-1) \\\
 -4 &= 4 \cdot (-1) + 6 \cdot 0 \\\
 -2 &= 4 \cdot 1    + 6 \cdot (-1) \\\
  0 &= 4 \cdot 0    + 6 \cdot 0 \\\
  2 &= 4 \cdot (-1) + 6 \cdot 1 \\\
  4 &= 4 \cdot 1    + 6 \cdot 0 \\\
  6 &= 4 \cdot 0    + 6 \cdot 1 \\\
  8 &= 4 \cdot 2    + 6 \cdot 0 \\\
 10 &= 4 \cdot 1    + 6 \cdot 1 \\\
\cdots
\end{align}
$$

これは, $$4$$と$$6$$の最大公約数である$$2$$の倍数の集合 $$2\mathbb{Z}$$と等しそうである. この予想は正しいだろうか.

**定理** 任意の整数$$a, b$$に対して, ある整数$$x, y$$が存在して,

$$
ax+by=gcd(a, b)
$$

**証明** $$I=a\mathbb{Z}+b\mathbb{Z}$$ とおく.

$$I$$の正の最小の要素を$$d$$とすると, 任意の$$x \in I$$について, 整数の除法の一意性により


$$
x=qd+r, 0 \le r \lt d
$$


を満たす$$q, d$$が一意に存在する.

$$d$$ は $$I$$ の要素なのだから, 適当な $$y, z$$ があって,


$$
d=ay+bz
$$


と表すことができる. ゆえに, 両辺の左から $$q$$ をかけることにより,


$$
\begin{align}  
&qd = q\cdot (ay + bz) \\\
\Leftrightarrow \ &qd =q\cdot ay + q\cdot bz \hspace{12pt}(分配律) \\\
\Leftrightarrow \ &qd =a\cdot qy+b\cdot qz \in I \\\
&(交換律. また, 明らかに qy \in \mathbb{Z}, qz \in \mathbb{Z} である) \\\
\end{align}
$$


$$x=qd+r$$ の両辺の左から $$-qd$$ を加えることによって,


$$
\begin{align}  
&-qd+x=-qd+qd+r \\\
\Leftrightarrow \ &-qd + x = 0 + r = r \\\
\Leftrightarrow \ &x + (-qd) = r \\\
&(整数の加法は可換なので, \\\
&-qd と x の和は入れ替えられる)  
\end{align}
$$


この左辺は, $$x \in I$$ および $$-qd \in I$$ より,いずれも$$as + bt$$,$$as^{\prime} +bt^{\prime}$$ のように表せるのだから,  
その和もまた $$as^{\prime \prime} + bt^{\prime \prime}$$ のように表せる. ゆえに,


$$
(左辺) \in I
$$


であり, したがって,


$$
(右辺)=r \in I
$$


である.

$$0 \lt r \lt d$$ を仮定すると, $$d$$ の最小性の仮定に矛盾するため, $$r = 0$$ である.

以上より, 任意の $$x \in I$$ は,


$$
x \in d \mathbb{Z} = \{ \cdots , -3d, -2d, -d, 0, d, 2d, 3d, \cdots \}
$$


このことは, すべての $$x \in I $$ に対して,


$$
\begin{align}  
d\ |\ x \hspace{20pt} (d は x の約数)  
\end{align}
$$


であることを意味している.


$$
\begin{align}  
a &= a \cdot 1 + b \cdot 0 \in I \\\
b &= a \cdot 0 + b \cdot 1 \in I  
\end{align}
$$


であるから, $$d | a$$ かつ $$d | b$$ すなわち $$d$$ は $$a, b$$ の公約数であり, すべての公約数は最大公約数の約数であるから,


$$
d\ |\ gcd(a, b)
$$


ところで, $$d \in I$$ より, ある$$y, z$$があって, $$d = ay + bz$$ と表せるのであった.

公約数の定義から, $$gcd(a, b) | a$$ かつ $$gcd(a, b) | b$$ なのだから,


$$
gcd(a, b)\ |\ ay + bz = d
$$


ゆえに,


$$
d\ |\ gcd(a, b) \hspace{16pt} かつ \hspace{16pt} gcd(a, b)\ |\ d
$$


が得られ, このことから,


$$
d = gcd(a, b)
$$

よって,


$$
x \in I \Rightarrow x \in gcd(a, b)\mathbb{Z}
$$

逆
に, $$x \in gcd(a, b)\mathbb{Z}$$ であれば $$x \in I$$である.

というのも, $$d (=gcd(a, b))$$ は $$I$$ の要素なのだから, うまく$$x, y$$を選べば$$d = ax + by$$ とすることができる. ゆえに $$z \in gcd(a, b)\mathbb{Z}$$ であれば, ある$$k$$があって

$$
\begin{align}
z &= k \cdot gcd(a, b) = k \cdot (ax + by) \\\
&= a\cdot kx + b \cdot ky \in I
\end{align}
$$

以上より,

$$x \in I$$ であれば $$x \in gcd(a, b)\mathbb{Z}$$ であり, かつ, $$x \in gcd(a, b)\mathbb{Z}$$ であれば $$x \in I$$ である.

したがって, $$I = gcd(a, b)\mathbb{Z}$$ である.

換言すると, $$I$$ に属する数の中には, 必ず $$gcd(a, b) = 1\cdot gcd(a, b) \in gcd(a, b)\mathbb{Z}$$ と等しいものが存在する.

このことは, 任意の $$a, b$$ に対して, うまく $$x, y$$ を選ぶことで, $$ax + by = gcd(a, b)$$ にできることを意味している ■