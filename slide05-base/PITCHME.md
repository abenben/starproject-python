### Pythonによるアルゴリズムと数学

2020年10月6日[Tue] / STAR Project

阿部一也

---

### アジェンダ

* お知らせ
* アルゴリズムについて
* 数学について

---

### お知らせ

* [みんなのPython勉強会 #62](https://startpython.connpass.com/)
  * 10/14（水） <br>若手を応援！
* [VUCA Labo #007](https://vucalabo.connpass.com/)
  * 10/21（水） <br>循環型で持続可能な地方でのデザイン

+++

### みんなのPython勉強会 #62(1/2)

https://startpython.connpass.com/event/187062/

<img src="/slide05-base/images/stapy_64_1.png" height="480">

+++

### みんなのPython勉強会 #62(2/2)

<img src="/slide05-base/images/stapy_64_2.png" height="480">

+++

### VUCA Labo #007

https://vucalabo007.peatix.com/

<img src="/slide05-base/images/vucalabo_007.jpg" height="480">

---

### アルゴリズムや数学に関するPython書籍

<a href="https://gihyo.jp/book/2020/978-4-297-11686-6"><img src="/slide05-base/images/pybook1.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4065178037"><img src="/slide05-base/images/pybook2.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/pybook3.jpg" height="150"></a><br>
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/pybook4.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/pybook5.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/pybook6.jpg" height="150"></a>

---

# アルゴリズム

+++

### アルゴリズムとは何か

* 計算や作業を遂行するための手順
* 特定の料理をつくためのレシピのようなもの
* 特定の問題を解くための手段がコンピューターとしての**アルゴリズム**
* 「プログラム」とは、コンピューターを実行するための手続き（専用の言語）

+++

### アルゴリズムを覚えると様々な課題が解決できる

<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/book2.jpg" height="350"></a>　
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/book1.jpeg" height="350"></a>

+++

### アルゴリズムの種類

* データ構造
* ソート
* 配列の探索
* グラフの探索
* セキュリティーアルゴリズム
* クラスタリング
* 機械学習
* その他

+++

### 例：名前でソート

``` 
import pprint

l = [{'Name': 'Alice', 'Age': 40, 'Point': 80},
     {'Name': 'Bob', 'Age': 20},
     {'Name': 'Charlie', 'Age': 30, 'Point': 70}]
pprint l
#
#
#

pprint.pprint(sorted(l, key=lambda x: x['Age'], reverse=True))
# [{'Age': 40, 'Name': 'Alice', 'Point': 80},
#  {'Age': 30, 'Name': 'Charlie', 'Point': 70},
#  {'Age': 20, 'Name': 'Bob'}]
```

---

# 数学

+++

### 数学の種類（高校レベル）

* 数
* 演算
* 方程式
* ベクトル
* 行列
* 集合と確率
* 統計と乱数
* 微分・積分

+++

### Pythonの数学ライブラリ

* [math](https://docs.python.org/ja/3/library/math.html)
* [numpy](https://numpy.org/doc/1.19/)
* [pandas(*一部の機能として内蔵)](https://pandas.pydata.org/docs/#)
* [sympy](https://docs.sympy.org/latest/index.html)
* [scipy](https://docs.scipy.org/doc/scipy-1.5.2/reference/)

+++

### 例：連立方程式を解く

a + b = 1　・・・①
5a + b = 3　・・・②
aとbの解は？

```
from sympy import Symbol, solve

a = Symbol('a')
a = Symbol('b')
ex1 = a + b - 1
ex2 = 5*a + b - 3

print(solve(ex1,ex2))

```

+++

太郎と花子は、リンゴとバナナを購入する予定です。
コンビニとデパートでそれぞれ購入するといくかになりますか？

### 例：行列の計算(1/2)

* 行列A

|名前|リンゴ|バナナ|
|---|---|---|
|太郎|1個|3個|
|花子|2個|1個|

* 行列B

|品名|コンビニ|デパート|
|---|---|---|
|リンゴ|150円|250円|
|バナナ|130円|230円|

+++

* 行列A × 行列B

|品名|コンビニ|デパート|
|---|---|---|
|太郎|540円|940円|
|花子|430円|730円|

### 例：行列の計算(1/2)

```
A = np.matrix[[1,3],[2,1]])
B = np.matrix([[150, 250],「130,230]])
A * B
matrix([[540, 940],
        [530, 730]])
```

---

### Pythonのドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)

---

### まとめ

* アルゴリズムを覚えると様々な課題が解決できる
* 数学ができるとムダを省ける
* 自作するより、パッケージやライブラリを覚えて使いこなすとさらに効率的

---

### (参考)Pythonドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)

---

### 来週の講義

