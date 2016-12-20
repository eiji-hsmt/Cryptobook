## RSA暗号

RSA暗号はもっとも古い公開鍵暗号で、1974年頃にイギリスの諜報機関GHCQのJ.エリスらが考案した暗号方式です。もっとも、それは国家機密として公となることはなく、RSA暗号は1977年に独自に再発見したRivest, Shamir, Adlemanのイニシャルからとって命名されています。RSA暗号のアルゴリズムは次の通りです。

相異なる素数$$p, q$$ \(できれば桁数がほぼ同じで、かつ $$gcd(p-1, q-1)=2$$となるものが好ましいとされている\) を生成し、整数 $$(p-1)(q-1)$$ と互いに素な整数 $$e$$ を選び、
$$
ed \equiv 1 \pmod{(p-1)(q-1)}
$$
を満たす整数 $$d$$ を求めておく。このような整数$$d$$の存在は、ベズーの補題によって保証され、拡張ユークリッド互除法 \(多項式時間アルゴリズム\) で求めることができる。 $$n := pq$$ \(RSAモジュールとよぶ\) として、 $$(n, e)$$ を公開鍵として公開する。 $$d$$ は秘密鍵として使用し、 $$p, q$$ は秘密にしておく。

暗号化するときは、平文 $$m$$ に対して、
$$
m^e \mod{n}
$$
を計算して、これを暗号文とする。

秘密鍵$$d$$をもっている人が、平文$$m$$の暗号文$$m^e$$を復号するときは、これを$$d$$乗する。すると、
$$
m^{ed} \equiv m \pmod{n}
$$
となって、平文を復号できる。

復号がこのようにうまくいくことは、 \(平文$$m$$が$$n$$と公約数をもつ場合を除いては\) フェルマーの小定理を一般化したオイラーの定理によって説明できる。

オイラーの定理によれば、

$$
gcd(m, pq) = 1
$$

のとき,

$$
m^{(p-1)(q-1)} \equiv 1 \pmod{pq}
$$

である.

ところで、$$ed \equiv 1 \pmod{(p-1)(q-1)}$$ の意味するところは、「$$ed$$を$$(p-1)(q-1)$$で割ると$$1$$余る」なのだから、ある整数$$k$$があって、

$$
ed = (p-1)(q-1)k + 1
$$

である。

よって、$$m$$と$$n (=pq)$$が互いに素のときは、

$$
m^{ed} = m^{(p-1)(q-1)k+1} = (m^{(p-1)(q-1)})^k \cdot m \equiv 1^k \cdot m \equiv m \pmod{n (=pq)}
$$

となり、復号できることが確かめられる。

$$m$$と$$n$$が互いに素でないときは、$$0 \le m \lt n$$であるから、$$m$$は$$n$$の倍数ではなく、$$n$$と$$1, -1$$以外の公約数をもつ. すなわち,

$$
gcd(m, n) = p
$$

あるいは、

$$
gcd(m, n) = q
$$

$$gcd(m,n)=p$$とおく。$$=q$$のときも同様にして証明できる。このようにおいても一般性を失わない。

このとき、ある$$k \in \mathbb{Z}$$があって、

$$
m = kp
$$

である。整数の除算は常に可能なのだから、適当な$$j, r$$があって、

$$
m = jq + r, 0 \le r \lt q
$$

でもある.

$$p, q$$が相異なる素数であることから、$$gcd(p, q) = 1$$であり、ベズーの補題より、ある整数$$s, t$$があって、

$$
ps + qt = 1
$$

である。同じことだが、

$$
ps \equiv 1 \pmod{q} \\\
qt \equiv 1 \pmod{p}
$$

であることに注意する.

以上から、$$m^\prime = m^{ed}$$ が $$\mod{n}$$ のもと \($$n$$を法として\), $$m^\prime \equiv m$$ となることを証明できる.

$$
m^\prime \equiv m^{ed} \equiv 0 \pmod{p}
$$

であり、

$$
\begin{align}
m^\prime &\equiv m^{ed} \equiv r^{ed} \pmod{q} \\\
&\equiv (r^{q-1})^{k(p-1)+1} \\\
&\equiv (r^{q-1})^{k(p-1)}\cdot r \\\
&\equiv r \pmod{q}
\end{align}
$$

である。\(後半はフェルマーの小定理により、$$r^{q-1} \equiv 1 \pmod{q}$$ であることを利用した。\)

よって、$$m^\prime$$は連立合同式

$$
m^\prime \equiv 0 \pmod{p} \\\
m^\prime \equiv r \pmod{q}
$$

を満たす。このような連立合同式の解法は [中国の剰余定理](chinese-remainder-theorem.md) にて解説したとおりであり、解は次のかたちになる。

$$
\begin{align}
m^\prime &\equiv 0\cdot \frac{p\cdot q}{p} \cdot y_p + r\cdot \frac{p \cdot q}{q} \cdot y_q \\\
&\equiv rpy_q \pmod{n \  (=pq)}
\end{align}
$$

ただし,

$$
\begin{align}
&\frac{p\cdot q}{p}\cdot y_p =qy_p \equiv 1 \pmod{p} \\\
&\frac{p\cdot q}{q}\cdot y_q =py_q \equiv 1 \pmod{q}
\end{align}
$$

とする.

$$
ps \equiv 1 \pmod{q}
$$

であったから、

$$
ps \equiv py_p \equiv 1 \pmod{q}
$$

であり、上式の$$py_q$$を$$ps$$に置き換えると,

$$
m^\prime \equiv rps \pmod{n}
$$

ここに、

$$
m = kp = jq + r \Rightarrow r = kp - jq
$$

を代入して、

$$
\begin{align}
m^\prime &\equiv rps \equiv (kp - jq)ps \pmod{n} \\\
&\equiv kpps - js\cdot pq \\\
&\equiv kpps \pmod{n \ (=pq)}
\end{align}
$$

右辺に,

$$
ps + qt = 1 \Rightarrow ps = 1 - qt
$$

を代入して,

$$
\begin{align}
m^\prime &\equiv kp (1 - qt) \\\
         &\equiv kp - kt\cdot pq \\\
         &\equiv kp \pmod{n \ (=pq)} \\\
         &\equiv m \pmod{n}
\end{align}
$$

以上より、$$gcd(m, n) \ne 1$$の場合 \(互いに素でない場合\) であっても、復号できることがわかった。