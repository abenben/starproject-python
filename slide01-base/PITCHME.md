### Pythonの基本知識

2020年8月4日 / STAR Project

阿部一也

<!-- https://docs.google.com/document/d/1sfhGtTWzKcSUvPucC851jxF9c1DkW9GWb1MDCeDxWjU/edit -->

---

### アジェンダ

* Pythonコミュニティについて
* Pythonについて
* 開発環境の準備方法

---

![alt](slide01-base/images/abenben.jpg)

+++
### Twitter

 [@abenben](https://twitter.com/abenben)

---

### Pythonコミュニティ

* [PyCon JP](https://pyconjp.connpass.com/event/181288/)
* [Start Python Club](https://startpython.connpass.com/)
* [fin-py](https://fin-py.connpass.com/)
* [Python もくもく会](https://mokupy.connpass.com/)

+++

### 技術コミュニティのメリット

* 触れたことのない技術を知る機会が増える
* 一緒に勉強する仲間を作れる
* 仕事や企業から引き合いがあったりする

---

### Pythonの人気

+++?image=slide01-base/images/pypl2020.png&size=auto 100%

---

### Pythonの特徴

* 文法がシンプルで可読性が高い
* コンパイルが不要
* 便利なライブラリが充実
* 便利なフレームワークが充実
* 専門分野での実績がある
* 将来性が高い
* 年収が高い！？

---

### Pythonのドキュメント

* [Pythonメインサイト日本語版](https://www.python.jp/)
* [Python言語リファレンス](https://docs.python.org/ja/3/reference/index.html)
* [Python標準リファレンス](https://docs.python.org/ja/3/library/)

---

### Google Colaboratory

* 学生、データ サイエンティスト、AI リサーチャーの皆さんの作業を効率化するツール。
* 今回の講義のような、学習ツールには最適な環境（個別に環境を準備しなくても済む）
* ただし、通常の仕事は、アプリケーションを開発する必要があるので、その場合は開発環境を整える必要がある（次ページを参照）。

---

### Python開発環境の整え方

* Pythonの環境について

+++

### Pythonインストール

* [`www.python.org/downloads`](https://www.python.org/downloads/)から公式版をインストール
  * WindowsはPATH設定のチェックを忘れずに
* 最新バージョンは3.8.3
* 2020年10月に3.9がリリース予定

+++

### 環境構築ガイド

* [`www.python.jp/install/install`](https://www.python.jp/install/install.html)

+++

### 他の手段

* Anaconda: [`www.anaconda.com`](https://www.anaconda.com/)
* pyenv: [`github.com/pyenv/pyenv`](https://github.com/pyenv/pyenv)
* Homebrew: [`brew.sh`](https://brew.sh/)
* Linux:
  * Ubuntu 20.04LTS: Python 3.8.2
  
+++

### Pythonインストール

* 特に理由がなければ公式版を使おう

---

### 仮想環境(venv)

+++

### 仮想環境(venv)

* [`docs.python.org/ja/3/library/venv`](https://docs.python.org/ja/3/library/venv.html)
* Pythonに標準でついてくる
* 常に使いましょう
* プロジェクト単位で使用パッケージを変えられる

+++

### venvの概念

* システムのPython
  * venv1
    * Django 3.0.7
  * venv2
    * Django 2.2.13

+++

### venv作成、有効化

* macOS、Linux
  * `python3.8 -m venv 環境名`
  * `source 環境名/bin/activate`

```sh
$ python3.8 -m venv env
$ source env/bin/activate
(env) $
```

+++

### venv作成、有効化

* Windows
  * `py -3.8 -m venv 環境名`
  * `環境名\Scripts\activate.ps1`
  * `環境名\Scripts\activate.bat`

```sh
> py -3.8 -m venv env
> env\Scripts\activate.ps1
(env) >
```

+++

### venvとは

* パスを書き換えているだけ
* 削除するときはフォルダーごと削除

+++

### venv無効化

* `deactivate`

```sh
(env) $ deactivate
$
```

+++

### 仮想環境(venv)

* パッケージをインストールするときは常に使おう

---

### パッケージ管理(pip)

+++

### パッケージ管理(pip)

* [`pip.pypa.io`](https://pip.pypa.io/en/stable/)
* サードパーティ製パッケージの管理ツール
* venvの中で使用するのが一般的

+++

### PyPI

* [`pypi.org`](https://pypi.org/)
* サードパーティー製パッケージの配布サイト
* 「パイピーアイ」と読むらしい

+++

### pipでインストール

* `pip install パッケージ名`
* 依存パッケージもまとめてインストール

```bash
(env) $ pip install beautifulsoup4
Collecting beautifulsoup4
  Downloading beautifulsoup4-4.9.1-py3-none-any.whl (115 kB)
     |████████████████████████████████| 115 kB 2.1 MB/s 
Collecting soupsieve>1.2
  Downloading soupsieve-2.0.1-py3-none-any.whl (32 kB)
Installing collected packages: soupsieve, beautifulsoup4
Successfully installed beautifulsoup4-4.9.1 soupsieve-2.0.1
```

+++

### pipでインストール

* バージョン指定
  * `pip install パッケージ名==バージョン`
* 最新にアップグレード
  * `pip install -U パッケージ名`

```bash
(env) $ pip install beautifulsoup4==4.8.0
: (省略)
      Successfully uninstalled beautifulsoup4-4.9.1
Successfully installed beautifulsoup4-4.8.0
(env) $ pip install -U beautifulsoup4
: (省略)
Successfully installed beautifulsoup4-4.9.1
```

@snap[north span-100]

+++
### パッケージ一覧を表示

* `pip list`
@snapend

@snap[north span-100]

+++
### 古いパッケージを確認

* `pip list -o`
@snapend

+++

### パッケージ一覧を再利用

* `pip freeze > requirements.txt`
* requirements.txtファイルをバージョン管理

```bash
(env) $ pip freeze > requirements.txt
(env) $ cat requirements.txt
beautifulsoup4==4.8.0
soupsieve==2.0.1
```

* 別の仮想環境でインストール
  * `pip install -r requirements.txt`

```bash
$ python3.8 -m venv newenv
$ source newenv/bin/activate
(newenv) $ pip install -r requirements.txt
(newenv) $ pip freeze
beautifulsoup4==4.8.0
soupsieve==2.0.1
```

+++

### アンインストール

* `pip uninstall -y パッケージ名`
* 依存パッケージは削除されない

```bash
(env) $ pip uninstall -y beautifulsoup4
Found existing installation: beautifulsoup4 4.8.0
Uninstalling beautifulsoup4-4.8.0:
  Successfully uninstalled beautifulsoup4-4.8.0
```

+++

### パッケージの探し方

* Awesome Python: [`awesome-python.com`](https://awesome-python.com/)

+++

### パッケージ管理(pip)

* pipコマンドを使いこなそう

---

### テキストエディター

+++

### テキストエディター

* 好きな物を使いましょう
  * シンタックスハイライト
  * TABでスペース4つ
* とくになければ以下がおすすめ
  * VSCode: [`code.visualstudio.com`](https://code.visualstudio.com/)
  * PyCharm: [`www.jetbrains.com/pycharm`](https://www.jetbrains.com/pycharm/)

---

### まとめ

* Python公式版
* venvで仮想環境
* pipでパッケージ管理
* テキストエディター

---

### ありがとうございました

@fab[twitter] [@abenben](https://twitter.com/abenben)
