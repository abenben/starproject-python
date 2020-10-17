### Pythonによるデータ処理

2020年10月20日[Tue] / STAR Project

阿部一也

---

### アジェンダ

* 特別講演
* お知らせ
* Pythonによるデータ処理
* まとめ
* 連絡事項

---

### 特別講演

* 寺田学さん

---

### お知らせ

* [Road to SiliconValley](https://event.svjp.org/)
  * 10/20(火) - 22（水）
* [VUCA Labo #007](https://vucalabo.connpass.com/)
  * 10/21（水） <br>循環型で持続可能な地方でのデザイン
* [みんなのPython勉強会 #62](https://startpython.connpass.com/)
  * 11/12（水） <br>（テーマ調整中）
+++

### Road to SiliconValley

https://event.svjp.org/

<img src="/slide05-base/images/event3.jpg" height="480">

+++

### VUCA Labo #007

https://vucalabo007.peatix.com/

<img src="/slide05-base/images/vucalabo_007.jpg" height="480">

+++

### みんなのPython勉強会 #63

https://startpython.connpass.com/event/192677

---

### データ処理に関するPython書籍

<a href="https://www.shoeisha.co.jp/book/detail/9784798158341"><img src="/slide06-base/images/pandas8.jpg" height="150"></a>　
<a href="https://www.oreilly.co.jp/books/9784873118451/"><img src="/slide06-base/images/pandas4.jpg" height="150"></a>　
<a href="https://gihyo.jp/book/2020/978-4-297-11568-5"><img src="/slide06-base/images/pandas7.jpg" height="150"></a>　
<a href="https://www.shuwasystem.co.jp/book/9784798058757.html"><img src="/slide06-base/images/pandas2.jpg" height="150"></a><br>　
<a href="https://www.shoeisha.co.jp/book/detail/9784798160672"><img src="/slide06-base/images/pandas5.jpg" height="150"></a>　
<a href="https://gihyo.jp/book/2018/978-4-7741-9647-3"><img src="/slide06-base/images/pandas3.jpg" height="150"></a>　
<a href="https://book.impress.co.jp/books/1118101067"><img src="/slide06-base/images/pandas1.jpg" height="150"></a>　
<a href="http://www.asakura.co.jp/books/isbn/978-4-254-12242-8/"><img src="/slide06-base/images/pandas6.jpg" height="150"></a>

---

# データ処理

* Numpy
* pandas（今日の講義はこちら）

+++

# Numpy

NumPyは科学技術計算に特化したサードパーティ製パッケージ

* 配列用の型であるndarray
* 行列用の型であるmatrix

+++

# pandas

pandasはPythonでのデータ分析のツールとして最も活用されており、データの入手や加工など多くのデータ処理に使われています。

* NumPyを基盤にシリーズ（Series）とデータフレーム（DataFrame）というデータ型を提供。
* pandasを利用する方法。

```python
>>> import pandas as pd
```

---

# シリーズ（Series）

Seriesは1次元データです。

```python
>>> ser = pd.Series([10, 20, 30, 40])
>>> ser
0 10
1 20
2 30
3 40
dtype: int64
```

+++

正確には、
シリーズはインデックス付けされた複数のデータ型（int、str、float等）を持つことが可能な1次元配列のオブジェクトです。

+++

# シリーズ：生成編

リストから生成

```python
>>> height = [170,172,165,180,174]
>>> ser = pd.Series(height)
>>> print(ser)
0 170
1 172
2 165
3 180
4 174
dtype: int64
```

+++

# シリーズ：生成編

Numpyから生成

```python
>>> import numpy as np
>>> height = np.array([170,172,165,180,174])
>>> ser = pd.Series(height)
>>> print(ser)
0 170
1 172
2 165
3 180
4 174
dtype: int64
```

+++

# シリーズ：生成編

インデックスにラベルを付けながら生成

```python
>>> name = ['sato','suzuki','tanaka','kato','watanabe']
>>> height = [170,172,165,180,174]
>>> ser = pd.Series(height,index=name)
>>> print(ser)
sato 170
suzuki 172
tanaka 165
kato 180
watanabe 174
dtype: int64
```

+++

# シリーズ：生成編

インデックス情報を取得

```python
>>> print(ser.index)
Index(['sato','suzuki','tanaka','kato','watanabe'],dtype: 'object')
```

+++

# シリーズ：生成編

ディクショナリから生成

```python
>>> dic {'sato':170,'suzuki']172,'tanaka':165,'kato':180,'watanabe':174}
>>> ser = pd.Series(dic)
>>> print(ser)
sato 170
suzuki 172
tanaka 165
kato 180
watanabe 174
dtype: int64
```

---

### データフレーム（DataFrame）

DataFrameは2次元のデータです。

```python
>>> df = pd.DataFrame([[10, "a", True],
>>> [20, "b", False,],
>>> [30, "c", False],
>>> [40, "d", True]])
>>> df
```

||0| 1| 2|
|---|---|---|---|
|0 |10 |a |True
|1 |20 |b |False
|2 |30 |c |False
|3 |40 |d |True

+++

### xxx

xxx

```python
>>>
```

---

### まとめ

* xxx
* xxx
* xxx

---

### (参考)Pythonドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)
* [numpyリファレンス](https://numpy.org/doc/stable/reference/)
* [pandasリファレンス](https://pandas.pydata.org/docs/reference/index.html)

---

### 次回のPython講義

『データベース操作』

2020/11/10(火) 19:00〜

---

### コアメンバーからのお知らせ
