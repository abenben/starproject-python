### Pythonによるデータ処理2

2020年11月10日[Tue] / STAR Project

阿部一也

---

### アジェンダ

* 特別講演
* お知らせ
* Pythonによるデータ処理2
* まとめ
* 連絡事項

---

### 特別講演

<img src="/slide07-base/images/murai-san.png" height="480">

---

### お知らせ

* [みんなのPython勉強会#63](https://startpython.connpass.com/event/192677/)
  * 11/12（木） 19:00-21:00<br>〜Pythonでみせる、つたえる。〜
* [VUCA Labo #7](https://peatix.com/event/1696240/view)
  * 11/26（木） <br>〜サスティナルブルな地域社会の創り方〜
* [フィンテックトレンド 2021（フィンテック養成勉強会#11）](https://fintech-engineer.connpass.com/event/193987/)
  * 12/11（金） <br>〜ニューノーマル時代に不可欠なコンパスを持ち歩く〜

+++

### みんなのPython勉強会 #63

https://startpython.connpass.com/event/192677/

<img src="/slide07-base/images/stapy63.png" height="480">

+++

### VUCA Labo #7

https://peatix.com/event/1696240/view

<img src="/slide07-base/images/vuca7.png" height="480">

+++

### フィンテックトレンド 2021

https://fintech-engineer.connpass.com/event/193987/

<img src="/slide07-base/images/finengine11.png" height="480">

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
* pandas その1
* pandas その2（今日の講義はこちら）

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

行と列はそれぞれ異なるラベルを持つ。数値や文字列など異なるデータ型を指定することも可能。

<img src="/slide06-base/images/dataframe.png" height="480">

+++

### データフレーム：生成編2

リストから生成

```python
>>> val = ['a',1,0.5]
>>> df = pd.DataFrame(val)
>>> df
    0
0    a
1    1
2    0.5
```

+++

### データフレーム：生成編3

2次元配列から生成

```python
>>> val = [[1,2,3],[4,5,6]]
>>> df = pd.DataFrame(val, index=['a','b'], columns=['c','d','e'])
>>> df
    c    d    e
a    1    2    3
b    4    5    6
```

+++

### データフレーム：生成編4

ディクショナリから生成

```python
>>> dic = {'a':[1,2,3], 'b':[4,5,6]}
>>> df = pd.DataFrame(dic)
>>> df
    a    b
0    1    4
1    2    5
2    3    6
```

+++

### データフレーム：生成編5

pandasのシリーズから生成

```python
>>> age_data = pd.Series([19,22,20], index=['sato','tanaka','suzuki'])
>>> sex_data = pd.Series(['F','M','F'], index=['sato','suzuki','watanabe'])
>>> df = pd.DataFrame({'age':age_data, 'sex':sex_data})
>>> df
    age    sex
sato    19.0    F
suzuki    20.0    M
tanaka    22.0    NaN
watanabe    NaN    F
```

+++

### データフレーム：生成編6

階層構造のあるディクショナリからまとめて生成

```python
>>> dics = {
>>>     'age':{'sato':19,'tanaka':22,'suzuki':20},
>>>     'sex':{'sato':'F','suzuki':'M','watanabe':'F'}
>>> }
>>> df = pd.DataFrame(dics)
>>> df
age    sex
sato    19.0    F
tanaka    22.0    NaN
suzuki    20.0    M
watanabe    NaN    F
```

+++

### データフレーム：ファイル読み込み

CSVやjson,htmlのテーブルなど様々なデータを読み込むことができます。

* オープンデータの取得 [札幌の住民基本台帳に基づく人口・世帯数のデータ](https://ckan.pf-sapporo.jp/dataset/juuki_3)
 * [今回は直近データを利用](https://ckan.pf-sapporo.jp/dataset/juuki_3/resource/0173c5fe-d7f6-4282-af39-a179addd6419)

```python
>>> df = pd.read_csv("https://ckan.pf-sapporo.jp/dataset/74351e60-a426-4ac1-b0cc-56cbcbbb9e92/resource/0173c5fe-d7f6-4282-af39-a179addd6419/download/ren202010.csv", index_col=0)
>>> df
世帯数    人口の総数    男の人口    女の人口
まちづくりセンター                
全市    1078155    1961682    916779    1044903
中央区    145872    239858    108663    131195
...    ...    ...    ...    ...
稲穂金山    8458    16873    7958    8915
星置    7240    15894    7472    8422```
```

+++

### データフレーム：クリーニング

読み込んだデータのゴミをクリーニングします。
今回は不要な行（行インデックスが"全市"）を削除します。

```python
>>> df.drop("全市",inplace=True)
>>> df
    世帯数    人口の総数    男の人口    女の人口
まちづくりセンター                
中央区    145872    239858    108663    131195
本府・中央    1565    2234    1005    1229
...    ...    ...    ...    ...
稲穂金山    8458    16873    7958    8915
星置    7240    15894    7472    8422
```

+++

### データフレーム：集計

列ごとの集計を行います。

```python
>>> df.sum()
世帯数      2156310
人口の総数    3923364
男の人口     1833558
女の人口     2089806
dtype: int64
```

+++

### データフレーム：統計量

列ごとに統計量を算出します。
* *describeは指数で表示されるので、pandas全体の表示フォーマットを変更します。*

```python
>>> pd.options.display.float_format = '{:.1f}'.format
>>> df.describe()
世帯数    人口の総数    男の人口    女の人口
count    97.0    97.0    97.0    97.0
mean    22230.0    40447.1    18902.7    21544.4
std    31862.0    57149.5    26745.7    30417.0
min    813.0    1099.0    549.0    550.0
25%    8430.0    16611.0    7645.0    8915.0
50%    14089.0    23917.0    11317.0    12923.0
75%    17928.0    33454.0    15228.0    17890.0
max    153699.0    285784.0    135802.0    149982.0
```

+++

### データフレーム：グラフ表示

グラフを表示します。
* *Colabにフォントが入っていないとエラーになります*

```python
>>> import matplotlib.pyplot as plt
>>> df['世帯数'].plot(kind="bar")
>>> plt.show()
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

### 次回のブロックチェーン講義

2020/11/17(火) 19:00〜

---

### 次回のPython講義

~~『データベース操作』~~

『データ処理（その2）』

2020/11/10(火) 19:00〜

---

### コアメンバーからのお知らせ
