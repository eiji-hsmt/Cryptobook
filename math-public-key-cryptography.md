# 公開鍵暗号の数学

公開鍵暗号は歴史的には1973年にイギリスの諜報機関であるGHCQのJ.エリスによって発見されたが、国家機密という扱いであり1997年まで公になることはなかった。その後、1976年にスタンフォード大学の研究者であったHellmanとその研究室の大学院生Diffieらによって「暗号化は容易いが、特定の利用者にしか知りえない情報なしに復号することは困難である」ような暗号方式のアイディアが提示され、1978年にMITのRivest, Shamir, AdlemanによってRSA暗号が再発見された。

公開鍵暗号は上記のように一方向の変換だけ容易いような関数によって実現され、それは初等的な数論に基づいている。ここでは、RSA暗号およびElGamal暗号を理解するために必要な最低限の数論の定理等を解説する。