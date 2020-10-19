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

### 特別講演（寺田学さん）

* 一般社団法人PyCon JP Association 代表理事
* 一般社団法人Pythonエンジニア育成推進協会 顧問理事
* Plone Foundation Ambassador
* PSF(Python Software Foundation) Fellow member 2019Q3 & Contributing members
* 株式会社CMSコミュニケーションズ 代表取締役
* 国立大学法人一橋大学　社会学研究科地球社会研究専攻　元客員准教授

+++

### 特別講演（寺田学さん）

プロフィール

```
1970年生まれ。
2005年にPython製WebサーバZope/Python製CMS Ploneに
 特化したCMSコミュニケーションズを起業。
国内でも早い段階からPythonでのシステム開発を手掛けており、
 Ploneのコアコミッターとしても活躍。
2010年にアジアで初めて開催されたPyCon APAC 2010 シンガポールに参加し
 翌年には日本でPyCon JPを立ち上げ、
 現在は一般社団法人PyCon JP Association代表理事を務める。
機械学習図鑑(翔泳社: 2019年4月)などPython著書・監修も多数手掛けている。
最近はPythonをはじめとした技術話題を気軽に発信する
 Podcast「terapyon channel」を配信中。
 https://podcast.terapyon.net/
* Twitter: @terapyon
```

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

<img src="/slide06-base/images/stapy63.png" height="480">

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

## データ処理

* Numpy
* pandas（今日の講義はこちら）

+++

## Numpy

NumPyは科学技術計算に特化したサードパーティ製パッケージ

* 配列用の型であるndarray
* 行列用の型であるmatrix
* Numpyを利用する方法。

```python
>>> import numpy as np
```

+++

## pandas

pandasはPythonでのデータ分析のツールとして最も活用されており、データの入手や加工など多くのデータ処理に使われています。

* NumPyを基盤にシリーズ（Series）とデータフレーム（DataFrame）というデータ型を提供。
* pandasを利用する方法。

```python
>>> import pandas as pd
```

---

### シリーズ（Series）：生成編1

Seriesは1次元データです。

```python
>>> ser = pd.Series([10, 20, 30, 40])
>>> print(ser)
0 10
1 20
2 30
3 40
dtype: int64
```

+++

正確には、
シリーズはインデックス付けされた複数のデータ型（int、str、float等）を持つことが可能な1次元配列のオブジェクトです。

<img src="/slide06-base/images/series.png" height="480">


+++

### シリーズ：生成編2

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

### シリーズ：生成編3

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

### シリーズ：生成編4

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

### シリーズ：生成編4-1

インデックス情報を取得

```python
>>> print(ser.index)
Index(['sato','suzuki','tanaka','kato','watanabe'],dtype: 'object')
```

+++

### シリーズ：生成編5

ディクショナリから生成

```python
>>> dic = { 'sato':170, 'suzuki':172, 'tanaka':165, 'kato':180, 'watanabe':174 }
>>> ser = pd.Series(dic)
>>> print(ser)
sato        170
suzuki      172
tanaka      165
kato        180
watanabe    174
dtype: int64
```

+++

### シリーズ：データの参照1

インデックス指定によるデータ参照

```python
>>> ser['tanaka']
165
```

+++

### シリーズ：データの参照2

インデックスをスライスで指定してデータ参照

```python
>>> ser['suzuki':'kato']
suzuki    172
tanaka    165
kato      180
dtype: int64
```

+++

### シリーズ：データの参照3

インデックスや位置インデックスを指定したデータ参照

```python
>>> print(ser['tanaka'])
>>> print(ser.iloc[2])
165
165
```

+++

### シリーズ：データの参照4

条件を指定してデータ参照

```python
>>> ser[ser > 170]
suzuki      172
kato        180
watanabe    174
dtype: int64
```

+++

### シリーズ：演算1

演算（乗算*）

```python
>>> print("*** 乗算 ***")
>>> print(ser * 2)
>>> print("*** 元データは変わっていない ***")
>>> print(ser)
*** 乗算 ***
sato        340
suzuki      344
tanaka      330
kato        360
watanabe    348
dtype: int64
*** 元データは変わっていない ***
sato        170
suzuki      172
tanaka      165
kato        180
watanabe    174
dtype: int64
```

+++

### シリーズ：演算2

加算追加

```python
>>> ser *= 2
>>> print(ser)
乗算追加
sato        340
suzuki      344
tanaka      330
kato        360
watanabe    348
dtype: int64
```

+++

### シリーズ：要素の追加(1/2)

前準備
要素前の元データの準備

```python
>>> #初期データの準備
>>> dic = { 'abe':70, 'inoue':65, 'ueda':76 }
>>> ser = pd.Series(dic)
>>> print(ser)
abe      70
inoue    65
ueda     76
dtype: int64
```

+++

### シリーズ：要素の追加(2/2)

要素を追加する
※注意：元データには反映されない

```python
>>> ser2=pd.Series([79,52],index=['endo','okada'])
>>> print(ser.append(ser2))
abe      70
inoue    65
ueda     76
endo     79
okada    52
dtype: int64
```

+++

### シリーズ：要素の変更

要素を追加する
※注意：元データが変わる

```python
>>> ser *= 2
>>> print(ser)
乗算追加
sato        340
suzuki      344
tanaka      330
kato        360
watanabe    348
dtype: int64
```

+++

### シリーズ：要素の削除
※注意：元データが変わる

```python
>>> del ser['abe']
>>> ser
noue    65
ueda     76
dtype: int64
```

+++

### シリーズ：重複データの削除(1/2)

前準備
要素前の元データの準備

```python
>>> # （このまま実行：初期データの準備）
>>> dic = { 'A':1, 'B':2, 'C':3, 'D':1, 'E':5 }
>>> ser = pd.Series(dic)
>>> ser
A    1
B    2
C    3
D    1
E    5
dtype: int64
```

+++

### シリーズ：重複データの削除(2/2)

```python
>>> ser.drop_duplicates(keep='first')
A    1
B    2
C    3
E    5
dtype: int64
```

+++

### シリーズ：欠損データの削除(1/2)

前準備
要素前の元データの準備

```python
>>> # （このまま実行：初期データの準備）
>>> dic = { 'A':1, 'B':np.nan, 'C':3, 'D':4, 'E':5 }
>>> ser = pd.Series(dic)
>>> ser
A    1.0
B    NaN
C    3.0
D    4.0
E    5.0
dtype: float64
```

+++

### シリーズ：欠損データの削除(2/2)

```python
>>> ser.dropna()
A    1.0
C    3.0
D    4.0
E    5.0
dtype: float64
```

+++

### シリーズ：統計量

前準備
要素前の元データの準備

```python
>>> dic = { 'sato':170, 'suzuki':172, 'tanaka':165, 'kato':180, 'watanabe':174 }
>>> ser = pd.Series(dic)
>>> ser.describe()
count      5.000000
mean     172.200000
std        5.495453
min      165.000000
25%      170.000000
50%      172.000000
75%      174.000000
max      180.000000
dtype: float64
```

---

### データフレーム：生成編1

データフレーム（DataFrame）は
2次元のデータが扱えます。

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

### データフレーム：生成編2

リストから生成

```python
>>>
```

+++

### データフレーム：生成編3

2次元配列から生成

```python
>>>
```

+++

### データフレーム：生成編4

ディクショナリから生成

```python
>>>
```

+++

### データフレーム：生成編5

pandasのシリーズから生成

```python
>>>
```
---

### まとめ

* データ処理にはNumpyやpandasを使う
* 1次元のデータ処理には、pandasのシリーズが使える
* 2次元のデータ処理には、pandasのデータフレームが使える

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
