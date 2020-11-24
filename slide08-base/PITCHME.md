### SQL操作

2020年11月24日[Tue] / STAR Project

阿部一也

---

### アジェンダ

* 特別講演
* お知らせ
* SQL操作
* まとめ
* 連絡事項

---

### 特別講演（井﨑武士 先生）

<img src="/slide08-base/images/izaki-san.jpg" height="480">

---

### お知らせ

* [VUCA Labo #7](https://peatix.com/event/1696240/view)
  * 11/26（木） 20:00〜21:30
    * 〜サスティナルブルな地域社会の創り方〜
* [みんなのPython勉強会#64](https://startpython.connpass.com/event/195410/)
  * 12/09（水） 19:00〜21:00
* [Fin-JAWS](https://fin-jaws.connpass.com/event/195041/)
  * 12/09（水） 19:00〜21:00
* [フィンテックトレンド 2021](https://fintech-engineer.connpass.com/event/193987/)
  * 12/11（金） 19:00〜21:30
    * 〜ニューノーマル時代に不可欠なコンパスを持ち歩く〜
* [X-Tech JAWS]
  * 12/21（月） 19:00〜21:00
* [Fin-JAWS]
  * 12/22（火） 19:00〜21:00

+++

### [11/26]VUCA Labo #7

https://peatix.com/event/1696240/view

<img src="/slide07-base/images/vucalabo07.png" height="480">

+++

### [12/11]フィンテックトレンド 2021

https://fintech-engineer.connpass.com/event/193987/

<img src="/slide08-base/images/fin11.jpg" height="480">

---

### データベースに関するお薦め図書

<a href="https://www.amazon.co.jp/dp/4798144452"><img src="/slide08-base/images/sql3.jpg" height="200"></a>　
<a href="https://www.amazon.co.jp/dp/4295005096"><img src="/slide08-base/images/SQL1.jpg" height="200"></a>　
<a href="https://www.amazon.co.jp/dp/4839961263"><img src="/slide08-base/images/sql2.jpeg" height="200"></a>　

---

## データ処理

* データベースとは
* SQLの種類
* データベースの準備
* データベースの操作
 * 追加
 * 検索
 * 変更
 * 削除

---

## データベース（DB）とは

データベースとは、簡潔にいえば、「データをアプリケーションソフトウェアとは独立して整理・収集・管理するシステム」のことです。

```
自分で書いたプログラムそのものが、データの保管や管理をするのではなく、
データの扱いについては、別のシステム、
つまりデータベースに任せるのが主流です。
DB（デービー）とも呼ばれる。
```

+++

## DBMS

データベース（DB）とは概念のことで、
実際に実現いているシステムは
DBMS（DataBaseManagementSystem）という。

+++

## データベースの種類

* リレーショナル型データベース
* 階層型データベース
* ネットワーク型データベース

+++

## リレーショナル型データベース

* RDBMS（Relational DataBaseManagementSystem）という
* 3つの中で最も一般的
* Excelのような２次元表データの集まりをリレーショナルで管理する、

+++

## RDBMSの種類

* Oracle Databas（有償：サポートあり）
* MicroSoft SQLServer（有償：サポートあり）
* PostgreSQL（無償：OSS）
* MySQL（無償：OSS）
* SQLite（無償：OSS）
* ほかにもたくさんある

+++

## RDBMSの機能

* 表テーブル
* データベースエンジン
* SQL（問い合わせ言語）

+++

## 表テーブル

* リレーショナルデータベースは、データを「表（テーブル）」に格納します。
* Excelのイメージと同じ。
リレーショナルデータベースは、データを「行（Row､Record）」と
「列（Field､Column）」の2次元の構造で格納します。
「行」と「列」を指定することにより、取り出したいデータの値を取得します。

+++

## データベースエンジン

PC側（プログラム実行部分）からのリクエストは、
いったん「データベース・エンジン」に渡されて、
クライアントに代わってデータベースへの処理を行う。
（表とユーザーの仲介役です）

+++

## SQL

データベースのテーブルを作ったり、テーブルにデータを登録したり、検索したり、更新ができる専用の言語

+++

## SQLの分類

* データ定義言語（通称DDL：DataDefinition Language）
* データ操作言語（通称DML：DataManipulation Language）
* データ制御言語（通称DCL：DataControlLanguage）

---

## SQLの種類

データ定義、データ操作、データ制御の主な言語について

+++

### 主なデータ定義言語（DDL）

* CREATE
* ALTER
* DROP
* RENAME
* TRUNCATE

+++

#### CREATE文（DDL）

テーブルを作成する

```
CREATE TABLE テーブル名 ( フィールド定義, フィールド定義,... )
```

+++

#### DROP文（DDL）

テーブルを削除する

```
DROP TABLE テーブル名
```

+++

### 主なデータ定義言語（DML）

* SELECT
* INSERT
* UPDATE
* DELETE

+++

#### SELECT文（DML）

データを参照するSQL文

```
SELECT   列名, 列名, …
FROM     表名
WHERE    列名 =(比較演算子) 値
ORDER BY ソート列 (ASC / DESC)
```

+++

#### INSERT文（DML）

データを追加するSQL文

```
INSERT  INTO 表名 (列1, 列2, 列3・・・)
VALUES            (値1, 値2, 値3・・・) ;
```

+++

#### UPDATE文（DML）

データを更新するSQL文

```
UPDATE  表名
SET    列名 = 値 
WHERE　更新する行を特定する条件;
```

+++

#### DELETE文（DML）

データを削除するSQL文

```
DELETE  FROM  表名
WHERE　削除する行を特定する条件;
```

+++

### 主なデータ制御言語（DCL）

* COMMIT
* ROLLBACK

---

#### SQLiteで動作確認

PythonからSQLiteに接続してSQLを操作してみよう

[チュートリアル8](tutorial09.ipynb)

---

### まとめ（SQL）

* データベースを利用するとみんなでデータが管理できる
* 大量のデータも管理できる
* データの追加・変更、参照にはSQL文を使う

---

### (参考)Pythonドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)
* [numpyリファレンス](https://numpy.org/doc/stable/reference/)
* [pandasリファレンス](https://pandas.pydata.org/docs/reference/index.html)

---

### 次回のブロックチェーン講義

* 『これからのデータ社会で活躍するために身につけるべきプライバシースキル』
* 2020/12/15(火) 19:00〜

```
①プライバシーがなぜ重要なのか？（20分） 栗原 宏平さん
②ワークショップ：プライバシーを理解するワークショップ（40分） 
```
 
+++

### ゲスト 栗原 宏平さん

Privacy by Design Lab 代表理事

大学時代にマーケティングを専攻し、議員秘書やNPOでのイベント運営に携わる。CollaboGate JapanではCMOとして大企業向けのブロックチェーンIDのデータ認証基盤開発を行う。ビジネス、政府領域のブロックチェーン及びビジネス領域でのデータプライバシー専門家として、ユネスコを始め国際学会などで積極的に情報発信を行う。アメリカのワシントンDCを拠点に全世界に展開するNPO法人Government Blockchain Associationの日本代表を兼務。

---

### 次回のPython講義

2020/12/08(火) 19:00〜

* チュートリアル
 * 『データの可視化・Webデータの取得（API、スクレイピング）』

---

### コアメンバーからのお知らせ
