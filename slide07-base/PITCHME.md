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

### 特別講演（村井康介さん）

<img src="/slide07-base/images/murai-san.jpg" height="480">

---

### お知らせ

* [みんなのPython勉強会#63](https://startpython.connpass.com/event/192677/)
  * 11/12（木） 19:00〜21:00
    * 〜Pythonでみせる、つたえる。〜
* [VUCA Labo #7](https://peatix.com/event/1696240/view)
  * 11/26（木） 20:00〜21:30
    * 〜サスティナルブルな地域社会の創り方〜
* [フィンテックトレンド 2021](https://fintech-engineer.connpass.com/event/193987/)
  * 12/11（金） 19:00〜21:30
    * 〜ニューノーマル時代に不可欠なコンパスを持ち歩く〜

+++

### みんなのPython勉強会 #63

https://startpython.connpass.com/event/192677/

<img src="/slide07-base/images/stapy63.png" height="480">

+++

### VUCA Labo #7

https://peatix.com/event/1696240/view

<img src="/slide07-base/images/vucalabo07.png" height="480">

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
* **pandas その2（今日の講義はこちら）**
 * データ読み込み

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

### pandasによるデータ読み込み

以下のファイル形式等を読み込むことができる。

```
CSVファイル,TSVファイル
jsonファイル
EXCELファイル
htmlファイル内のテーブル
その他（テーブル形式、HDF5ファイルなど）
```

+++

#### CSV,TSV

* CSVファイル（カンマ区切りのファイル）
* TSVファイル（タブ区切りのファイル）

+++

#### PandasによるCSV,TSVの読み込み

* read_csv()を利用する
* read_csv()の主なオプション

<img src="/slide07-base/images/pandas-read_csv.png" height="480">

+++

### 1.1.1 CSVファイル読み込み

* [CSVファイル](https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv)はread_csvを利用する。

```python
[プログラム]
csv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv'
df=pd.read_csv(csv_file)
df
```

||店舗名|期首在庫数|売上数|仕入数|
|---|---|---|---|---|
|**0**|新宿店|100|50|100|
|**1**|池袋店|500|200|1000|
|**2**|銀座店|800|300|600|
|**3**|秋葉原店|300|100|500|
|**4**|大手町店|700|200|1000|

+++

#### 1.1.1(a) ヘッダー、カラムを指定

```python
[プログラム]
csv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv'
df=pd.read_csv(csv_file,index_col=0,header=0)
df
```

|**店舗名**|期首在庫数|売上数|仕入数|
|---|---|---|---|
|**新宿店**|100|50|100|
|**池袋店**|500|200|1000|
|**銀座店**|800|300|600|
|**秋葉原店**|300|100|500|
|**大手町店**|700|200|1000|

+++

#### 1.1.1(b) ヘッダー・カラムの指定無し

* Noneを指定する。

```python
[プログラム]
csv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv'
df=pd.read_csv(csv_file,index_col=None,header=None)
df
```

||0|1|2|3|
|---|---|---|---|---|
|**0**|店舗名|期首在庫数|売上数|仕入数|
|**1**|新宿店|100|50|100|
|**2**|池袋店|500|200|1000|
|**3**|銀座店|800|300|600|
|**4**|秋葉原店|300|100|500|
|**5**|大手町店|700|200|1000|


+++

#### 1.1.1(c) 任意のヘッダーを指定する

* namesを利用する。

```python
[プログラム]
csv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv'
df=pd.read_csv(csv_file, index_col=0, header=0,names=list(['店','在庫','売上','仕入']))
df
```

|**店**|在庫|売上|仕入|
|---|---|---|---|
|**新宿店**|100|50|100|
|**池袋店**|500|200|1000|
|**銀座店**|800|300|600|
|**秋葉原店**|300|100|500|
|**大手町店**|700|200|1000|

+++

#### 1.1.1(d) 列を絞って読み込む

```python
[プログラム]
csv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.csv'
df=pd.read_csv(csv_file, usecols=['店舗名','売上数'])
df
```

||店舗名|売上数|
|---|---|---|
|**0**|新宿店|50|
|**1**|池袋店|500|
|**2**|銀座店|300|
|**3**|秋葉原店|100|
|**4**|大手町店|200|

+++

#### 1.1.1(e) TSVファイル読み込み

* [TSVファイル](https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.tsv)は、セパレータにタブ（\t）を指定する。

```python
[プログラム]
tsv_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.tsv'
df=pd.read_csv(tsv_file, index_col=0,sep='\t')
df
```

||店舗名|期首在庫数|売上数|仕入数|
|---|---|---|---|---|
|**0**|新宿店|100|50|100|
|**1**|池袋店|500|200|1000|
|**2**|銀座店|800|300|600|
|**3**|秋葉原店|300|100|500|
|**4**|大手町店|700|200|1000|

+++

### 1.1.2 EXCEL読み込み

* [EXCEL](https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.xlsx)はread_excel()を利用する。

```python
[プログラム]
excel_file='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.xlsx'
df=pd.read_excel(excel_file)
df
```

||店舗名|期首在庫数|売上数|仕入数|
|---|---|---|---|---|
|**0**|新宿店|100|50|100|
|**1**|池袋店|500|200|1000|
|**2**|銀座店|800|300|600|
|**3**|秋葉原店|300|100|500|
|**4**|大手町店|700|200|1000|

+++

### 1.1.2 EXCEL読み込み（その２）

* read_excel()の中でxrldを利用するのでインストールが必要
* Google Colabでは事前にインストール済み

```shell
[コマンド]
pip install xrld
```

+++

### 1.1.3 jsonデータ読み込み

#### JSONとは

* JSONとはJavaScriptObjectNotationの略。
* データ定義文をベースとした軽量なデータ記述言語の1つ。
* JavaScript専用のデータ形式ではなう。
* 複数の言語間で円滑にデータの受け渡せるうように設計。
* JSONの詳しい扱い方は公式ドキュメントを参照ください。
* json.org URL : https://www.json.org/jsonja.html

+++

* [jsonファイル](https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.json)はread_json()を利用する。

```python
json_file2='https://github.com/abenben/starproject-python/raw/master/sampledata/tutorial05/store.json'
df=pd.read_json(json_file2)
df
```

||期首在庫数|売上数|仕入数|
|---|---|---|---|
|新宿店|100|50|100|
|池袋店|500|200|1000|
|銀座店|800|300|600|

+++

### 1.1.4 Webサイト上の表を読み込む

* io.html.read_html()を利用する。
* Webサイト上のテーブル(tableタグ)を読み込む
* 例：[Yahoo!株価情報（銘柄：日立）](https://stocks.finance.yahoo.co.jp/stocks/history/?code=6501.T)
* 複数まとめて読み込んでくれる（株価は２つ目のテーブル）

+++

```python
[プログラム]
from urllib.request import urlopen
url = 'https://stocks.finance.yahoo.co.jp/stocks/history/?code=6501.T'
f = urlopen(url)
html = f.read()
df = pd.io.html.read_html(html)
df[1]
```

||	日付|	始値|	高値|	安値|	終値|	出来高|	調整後終値*|
|--|--|--|--|--|--|--|--
|0	|2020年11月9日|	3548|	3606|	3548|	3591|	2175200|	3591|
|　：|：|：|：|：|：|：|：|


---

### pandasによるデータのマージ

複数のデータフレームに含まれる特定のカラムを基に1つにまとめることをマージという。

pandasのマージはmerge()を利用する。

+++

### 1.2.1 1対1のマージ（同じキー名） 

同じキー名でマージする場合は、mege関数のonオプションを利用する。

+++

元データ1（左側）

```python
[プログラム1]
leftdf = pd.DataFrame({
    '身長':[165,181,173],
    '体重':[56,68,73],
    '名前':['鈴木洋子','田中二郎','鈴木一郎'],
})
leftdf
```

||身長|体重|名前|
|-|-|-|-|
|0|165|56|鈴木洋子|
|1|181|68|田中二郎|
|2|173|73|鈴木一郎|

+++

元データ２（右側）

```python
[プログラム2]
rightdf = pd.DataFrame({
    '名前':['鈴木洋子','田中二郎','鈴木一郎'],
    '国語':[87,86,65],
    '数学':[83,90,74],
})
rightdf
```

||名前|国語|数学|
|-|-|-|-|
|0|鈴木洋子|87|83|
|1|田中二郎|86|90|
|2|鈴木一郎|65|74|

+++

データ1（右側）とデータ２（右側）をマージする

```python
[プログラム3]
pd.merge(leftdf,rightdf,on='名前')
```

|身長|体重|名前|国語|数学|
|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|
|1|181|68|田中二郎|86|90|
|2|173|73|鈴木一郎|65|74|


+++

### 1.2.2 1対1のマージ（キー名が異なる）

異なるキー名でマージする場合は、mege関数のleft_on,right_onオプションを利用する。

+++

元データ1（左側）

```python
[プログラム1]
leftdf = pd.DataFrame({
    '身長':[165,181,173],
    '体重':[56,68,73],
    '名前':['鈴木洋子','田中二郎','鈴木一郎'],
})
leftdf
```

||身長|体重|名前|
|-|-|-|-|
|0|165|56|鈴木洋子|
|1|181|68|田中二郎|
|2|173|73|鈴木一郎|

+++

元データ２（右側）

```python
[プログラム2]
rightdf = pd.DataFrame({
    '国語':[87,86,65],
    '数学':[83,90,74],
    '氏名':['鈴木洋子','田中二郎','鈴木一郎'],
})
rightdf
```

||国語|数学|氏名|
|-|-|-|-|
|0|87|83|鈴木洋子|
|1|86|90|田中二郎|
|2|65|74|鈴木一郎|

+++

キーの異なるデータ1（右側）とデータ２（右側）をマージする

```python
[プログラム3]
pd.merge(leftdf,rightdf,left_on='名前',right_on='氏名')
```

||身長|体重|名前|国語|数学|氏名|
|-|-|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|鈴木洋子|
|1|181|68|田中二郎|86|90|田中二郎|
|2|173|73|鈴木一郎|65|74|鈴木一郎|

+++

### 1.1.3 1対1のマージ（結合方法）

* 結合方法にはいくつかの種類がある。
* 結合方法(merge関数のhowオプション）

|howオプション|概要|
|-|-|
|inner|内部結合、両方のデータフレームの積集合|
|outer|外部結合、両方のデータフレームの和集合|
|left|１番目（左辺）のデータフレームのキーのみ使用|
|right|2番目（右辺）のデータフレームのキーのみ使用|

+++

元データ1（左辺）

```python
[プログラム1]
leftdf = pd.DataFrame({
    '身長':[165,181,173,160],
    '体重':[56,68,73,54],
    '名前':['鈴木洋子','田中二郎','鈴木一郎','斎藤美穂子'],
})
leftdf
```

||身長|体重|名前|
|-|-|-|-|
|0|165|56|鈴木洋子|
|1|181|68|田中二郎|
|2|173|73|鈴木一郎|
|3|160|54|鈴木一郎|

+++

元データ２（右側）

```python
[プログラム2]
rightdf = pd.DataFrame({
    '名前':['鈴木洋子','田中二郎','鈴木一郎','佐藤利夫'],
    '国語':[87,86,65,50],
    '数学':[83,90,74,61],
})
rightdf
```

||名前|国語|数学|
|-|-|-|-|
|0|鈴木洋子|87|83|
|1|田中二郎|86|90|
|2|鈴木一郎|65|74|
|3|佐藤利夫|50|61|

+++

#### 内部結合

```python
[プログラム3]
pd.merge(leftdf,rightdf,on='名前',how='inner')
```

||身長|体重|名前|国語|数学|氏名|
|-|-|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|鈴木洋子|
|1|181|68|田中二郎|86|90|田中二郎|
|2|173|73|鈴木一郎|65|74|鈴木一郎|

+++

#### 外部結合

```python
[プログラム4]
pd.merge(leftdf,rightdf,on='名前',how='outner')
```

||身長|体重|名前|国語|数学|氏名|
|-|-|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|鈴木洋子|
|1|181|68|田中二郎|86|90|田中二郎|
|2|173|73|鈴木一郎|65|74|鈴木一郎|
|3|160|54|斎藤美穂子|NaN|NaN|
|4|NaN|NaN|佐藤利夫|50.0|61.0|

+++

#### 左辺結合

```python
[プログラム5]
pd.merge(leftdf,rightdf,on='名前',how='left')
```

||身長|体重|名前|国語|数学|氏名|
|-|-|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|鈴木洋子|
|1|181|68|田中二郎|86|90|田中二郎|
|2|173|73|鈴木一郎|65|74|鈴木一郎|
|3|160|54|斎藤美穂子|NaN|NaN|

+++

#### 右辺結合

```python
[プログラム6]
pd.merge(leftdf,rightdf,on='名前',how='right')
```

||身長|体重|名前|国語|数学|氏名|
|-|-|-|-|-|-|-|
|0|165|56|鈴木洋子|87|83|鈴木洋子|
|1|181|68|田中二郎|86|90|田中二郎|
|2|173|73|鈴木一郎|65|74|鈴木一郎|
|4|NaN|NaN|佐藤利夫|50.0|61.0|

---

### まとめ

* pandasに様々なデータを取り込める
* 
* 

---

### (参考)Pythonドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)
* [numpyリファレンス](https://numpy.org/doc/stable/reference/)
* [pandasリファレンス](https://pandas.pydata.org/docs/reference/index.html)

---

### 次回のブロックチェーン講義

* 『学生時代に抑えたいフィンテックのポイント』
* 2020/11/17(火) 19:00〜

```
①ショートトーク1（10分） 藤井 達人さん
②ショートトーク2（10分） 堀口 純一さん
③ディスカッション（40分）
 藤井 達人さん
 堀口 純一さん
```
 
+++

### ゲスト1 藤井達人さん

<img src="/slide07-base/images/fujii.png" height="480">

+++

### ゲスト２ 堀口純一さん

<img src="/slide07-base/images/horiguchi.png" height="480">

---

### 次回のPython講義

2020/11/24(火) 19:00〜

* 特別講演
 * 井崎武士さん
   * **NVIDIA**エンタープライズ事業部事業部長
   * 日本ディープラーニング協会 理事

* チュートリアル
 * 『データベース操作』

---

### コアメンバーからのお知らせ
