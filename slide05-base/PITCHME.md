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
* [Road to SiliconValley](https://event.svjp.org/)
  * 10/20(火) - 22（水）
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

### Road to SiliconValley

https://event.svjp.org/

<img src="/slide05-base/images/event3.jpg" height="480">

+++

### VUCA Labo #007

https://vucalabo007.peatix.com/

<img src="/slide05-base/images/vucalabo_007.jpg" height="480">

---

### アルゴリズムや数学に関するPython書籍

<a href="https://gihyo.jp/book/2020/978-4-297-11686-6"><img src="/slide05-base/images/pybook1.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4065178037"><img src="/slide05-base/images/pybook2.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/pybook3.jpg" height="150"></a><br>
<a href="https://www.amazon.co.jp/dp/4822295915"><img src="/slide05-base/images/pybook4.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4873117682"><img src="/slide05-base/images/pybook5.jpg" height="150"></a>　
<a href="https://www.amazon.co.jp/dp/4797393963"><img src="/slide05-base/images/pybook6.jpg" height="150"></a>

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

<a href="https://www.amazon.co.jp/dp/4040800044"><img src="/slide05-base/images/book2.jpg" height="350"></a>　
<a href="https://www.amazon.co.jp/dp/482228493X"><img src="/slide05-base/images/book1.jpeg" height="350"></a>

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

### ソート

例：名前でソート

```python
import pprint

l = [{'Name': 'Suzuki', 'Age': 40, 'Point': 80},
     {'Name': 'Tanaka', 'Age': 26},
     {'Name': 'Watanabe', 'Age': 20},
     {'Name': 'Sato', 'Age': 30, 'Point': 70}]

print("[ソート前]")
pprint.pprint(l)
# [{'Age': 40, 'Name': 'Suzuki', 'Point': 80},
# {'Age': 26, 'Name': 'Tanaka'},
# {'Age': 20, 'Name': 'Watanabe'},
# {'Age': 30, 'Name': 'Sato', 'Point': 70}]

print("[ソート後]")
pprint.pprint(sorted(l, key=lambda x: x['Age'], reverse=True))
# [{'Age': 40, 'Name': 'Suzuki', 'Point': 80},
# {'Age': 30, 'Name': 'Sato', 'Point': 70},
# {'Age': 26, 'Name': 'Tanaka'},
# {'Age': 20, 'Name': 'Watanabe'}]
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
* [pandas](https://pandas.pydata.org/docs/#)(*一部の機能として内蔵)
* [sympy](https://docs.sympy.org/latest/index.html)
* [scipy](https://docs.scipy.org/doc/scipy-1.5.2/reference/)

+++

### 方程式

例：連立方程式を解く

a + b = 1　・・・①<br>
5a + b = 3　・・・②<br>
aとbの解は？<br>

```python
from sympy import Symbol, solve

a = Symbol('a')
b = Symbol('b')
ex1 = a + b - 1
ex2 = 5*a + b - 3

print(solve((ex1,ex2)))
# {a: 1/2, b: 1/2}
```

+++

### 行列（1/3）

例：行列の計算

太郎と花子は、リンゴとバナナを購入する予定です。<br>
コンビニとデパートでそれぞれ購入するといくかになりますか？<br>

+++

### 行列（2/3）

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

### 行列（3/3）

* 行列A × 行列B

|品名|コンビニ|デパート|
|---|---|---|
|太郎|540円|940円|
|花子|430円|730円|

```python
import numpy as np
A = np.matrix([[1,3],[2,1]])
B = np.matrix([[150,250],[130,230]])
A * B
#matrix([[540, 940],
#        [430, 730]])
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

### 来週のブロックチェーン講義

『トークンエコノミーによる循環型社会のデザイン』

2020/10/13(火) 19:00〜

<a href="https://www.amazon.co.jp/dp/4297100495"><img src="/slide05-base/images/kawamoto.png" height="400"></a>
