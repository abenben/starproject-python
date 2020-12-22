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
  * 2021年1月13日（水） 19:00〜21:00
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
* 1.2.Web APIサービス
* 1.3.クローリング

---

### 1.1.スクレイピング


* 1.1.1.robots.txt
* 1.1.2.requests
* 1.1.3.BeautifulSoup
* 1.1.4.pandasでテーブル取得
* 1.1.5 Selenium

+++

### 1.1.1.robots.txt

Webサイトではクローリングを制御するために
robots.txtが置かれている。
クローリング時は、この中のルールに従わねばならない。

```
!pip install reppy
```

```
from reppy.robots import Robots 

robots=Robots.fetch("https://allabout.co.jp/robots.txt")
agent=robots.agent("*")
agent.allowed("https://allabout.co.jp/r_finance/")
```

+++

### 1.1.2.requests

* Python の HTTP 通信ライブラリ。
* Webサイトの情報取得や画像の収集を簡単に行える

```
!pip install requests
```

```
import requests

url = "https://xxx"
response = requests.get(url)
print(response.text)
```

+++

### 1.1.3.BeautifulSoup

* HTMLやXMLからデータを引き出すことができるライブラリ
* HTMLを先頭からたどらずに、目的のidやclassを検索してその中から解析できるのがメリット

```
import requests
from bs4 import BeautifulSoup

# Webページを取得して解析する
load_url = "https://www.ymori.com/books/python2nen/test2.html"
html = requests.get(load_url)
soup = BeautifulSoup(html.content, "html.parser")

# title、h2、liタグを検索して、その文字列を表示する
print(soup.find("title").text)
```

+++

#### 1.1.4.pandasでテーブル取得

HTML上のテーブルタグはpandasの表に簡単に取り込める

```
import pandas as pd
url="https://info.finance.yahoo.co.jp/ranking/?kd=45"
df=pd.read_html(url)
df[0]
```

+++

#### 1.1.5 Selenium

Web ブラウザの操作を自動化するためのフレームワーク

```
pip install selenium
```

+++

```
from selenium import webdriver
from selenium.webdriver.firefox.options import Options
import time
url="https://hatenablog.com/"

options=Options()
options.binary_location = '/Applications/Firefox Developer Edition.app/Contents/MacOS/firefox'
options.add_argument('-headless')
driver = webdriver.Firefox(firefox_options=options)
driver.get(url)
width=driver.execute_script("returndocument.body.scrollWidth")
height=driver.execute_script("returndocument.body.scrollHeight")
driver.set_window_size(width,height)
time.sleep(3)
driver.save_screenshot("screenshot.png")
time.sleep(3)
driver.quit()
```

---

### 1.2.Web API サービス

HTTPプロトコルを用いてネットワーク越しに呼び出すアプリケーション間、システム間のインターフェースのこと。

例：無料天気予報APIのOpenWeatherMapを使ってみる

```
import requests
import json

# 現在の天気を取得する：東京
url = "http://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}&lang=ja&units=metric"
url = url.format(city="Tokyo,JP", key="XXXXXXXXXX")

jsondata = requests.get(url).json()
print("都市名   = ", jsondata["name"])
print("気温　　 = ", jsondata["main"]["temp"])
print("天気　　 = ", jsondata["weather"][0]["main"])
print("天気詳細 = ", jsondata["weather"][0]["description"])
```

---

### 1.3.クローリングとは

```
ロボット型検索エンジンにおいて、プログラムがインターネット上のリンクを辿ってWebサイトを巡回し、Webページ上の情報を複製・保存すること。
クローリングを行うためのプログラムを「クローラ」や「スパイダー」と呼ぶ。
```

+++

#### 1.3.1.scrapy

Python でクローラーを実装するためのフレームワークです

+++

```
pip install scrapy
```

```
# クローラープロジェクトの作成
scrapy startproject [プロジェクト名]
```

---

### 2.テキスト解析とは

* 2.1.PDFからテキスト抽出
* 2.2.形態素解析（MeCab）
* 2.3.形態素解析（janome）
* 2.4.ワードクラウド

---

#### 2.1.PDFからテキスト抽出

PDFファイルのテキスト文字列を抽出する方法
画像イメージのテキストは抽出できない

+++

```
# OSにインストール（Linux ubuntu）
apt install python3-pdfminer
```

```
!pip install pdfminer.six
```

+++

```
from pdfminer.pdfinterp import PDFResourceManager,PDFPageInterpreter
from pdfminer.converter import TextConverter
from pdfminer.layout import LAParams
from pdfminer.pdfpage import PDFPage

input_path="XXXXX.pdf"
output_path="YYYYY.txt"
rsrcmgr=PDFResourceManager()
codec="utf8"
params=LAParams()

with open(output_path,"ab") as output:
    device=TextConverter(rsrcmgr,output,codec=codec,laparams=params)
    with open(input_path,"rb") as input:
        interpreter=PDFPageInterpreter(rsrcmgr,device)
        for page in PDFPage.get_pages(input):
            interpreter.process_page(page)
        device.close()
```

---

### 2.2.形態素解析（MeCab）

文章を意味を持つ最小の単位（=形態素）に分け、それぞれのパーツの品詞などを判別する解析手法

```
>> 庭には二羽鶏がいます
庭 名詞,一般,*,*,*,*,庭,ニワ,ニワ
に 助詞,格助詞,一般,*,*,*,に,ニ,ニ
は 助詞,係助詞,*,*,*,*,は,ハ,ワ
二 名詞,数,*,*,*,*,二,ニ,ニ
羽 名詞,接尾,助数詞,*,*,*,羽,ワ,ワ
鶏 名詞,一般,*,*,*,*,鶏,ニワトリ,ニワトリ
が 助詞,格助詞,一般,*,*,*,が,ガ,ガ
い 動詞,自立,*,*,一段,連用形,いる,イ,イ
ます  助動詞,*,*,*,特殊・マス,基本形,ます,マス,マス
```

+++

```
# OSにMeCabと辞書をインストール（Linux ubuntu）
apt install aptitude
aptitude install mecab libmecab-dev mecab-ipadic-utf8 git make curl xz-utils file -y
```

```
pip install mecab-python3==0.7
```

+++

```
mecab = MeCab.Tagger ("-Ochasen")
text = mecab.parse ("すもももももももものうち")
print(text)
```

---

### 2.3.形態素解析（janome）

* メリット
 * パッケージのインストールのみで動く
* デメリット
 * MeCabの方が早い

+++

```
# janomeはパッケージのインストールのみで動かせる！
pip install janome
```

+++

```
from janome.tokenizer import Tokenizer
t = Tokenizer()
malist = t.tokenize("すもももももももものうち")
for n in malist:
    print(n)
```

---

### 2.4.ワードクラウド

文章中で出現頻度が高い単語を選んで、その頻度に応じた大きさで図示する手法のこと

<img src="/slide10-base/images/wordcloud.png" height="200">

+++

```
pip install wordcloud
```

```
wordcloud = WordCloud(
    font_path = fpath, # フォント
    width=900, height=600,   # サイズ
    background_color="white",   # 背景
    stopwords=set(stop_words), # 禁止ワード
    max_words=500,   # 最大単語表示数
    min_font_size=4,   # 最小フォント数
    collocations = False   #default = True
    ).generate(words_wakati) # 単語のリスト登録（重複ありで）
```

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

2021/1/（調整中）

* GitHub

---

### コアメンバーからのお知らせ

---

お疲れ様でした！
