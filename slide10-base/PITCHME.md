### スクレイピング・テキスト解析

2020年12月22日[Tue] / STAR Project

阿部一也

---

### アジェンダ

* お知らせ
* 1.スクレイピング
* 2.テキスト解析
* まとめ
* 連絡事項

---

### お知らせ

* [みんなのPython勉強会#65](https://startpython.connpass.com/event/198770/)
  * 2021年2/13（水） 19:00〜21:00
* [VUCA Labo](https://vucalabo.connpass.com/)
  * 2021年1月27日(水) 20:00〜20:30
* [フィンテックエンジニア養成勉強会](https://fintech-engineer.connpass.com/)
  * 2021年2月6日(金)19:00〜21:00

---

### スクレイピング・テキスト解析に関するお薦め図書

<a href="https://www.amazon.co.jp/dp/4798161918"><img src="/slide10-base/images/book1.jpg" height="200"></a>　
<a href="https://www.amazon.co.jp/dp/4844378864"><img src="/slide10-base/images/book2.jpg" height="200"></a>　

---

## 1.スクレイピング

* 1.1.スクレイピング
* 1.2.Webサービス
* 1.3.クローリング

---

### 1.1.スクレイピング


* 1.1.1.robots.txt
* 1.1.2.requests
* 1.1.3.BeautifulSoup
* 1.1.4.pandasでテーブル取得
* 1.1.5 Selenium

+++

#### 1.1.1.robots.txt

```
Webサイトは、クローリングを制御するために
robots.txtを置いている
この中のルールに従わねばならない
```

---

```
!pip install reppy
```

```
from reppy.robots import Robots 

robots=Robots.fetch("https://allabout.co.jp/robots.txt")
agent=robots.agent("*")
agent.allowed("https://allabout.co.jp/r_finance/")
```

---

#### 1.1.2.requests

```
Python の HTTP 通信ライブラリ。
Webサイトの情報取得や画像の収集を簡単に行える。
```

---

```
!pip install requests
```

```
import requests

url = "https://xxx"
response = requests.get(url)
print(response.text)
```

---

#### 1.1.3.BeautifulSoup

---

#### 1.1.4.pandasでテーブル取得

---

#### 1.1.5 Selenium

---

### 1.2.Webサービス


+++

#### 1.2.1.xxx

---

### 1.3.クローリングとは

+++

#### 1.3.1.scrapy

---

### 2.1.テキスト解析とは

+++

#### 2.1.1.xxx

---

#### まとめ（スクレイピング・テキスト解析）

* xxxxx
* yyyyy
* zzzzz

---

### (参考)Pythonドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)
* [numpyリファレンス](https://numpy.org/doc/stable/reference/)
* [pandasリファレンス](https://pandas.pydata.org/docs/reference/index.html)

---

### 次回のPython講義

2021/1/未定

* GitHub

---

### コアメンバーからのお知らせ

---

お疲れ様でした！
