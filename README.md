# ONE PIECE悪魔の実検索システム（heroku deploy版）
## 概要
search_onepieceをherokuを用いてdeployを試みました．
今回使用しているデータベースNeo4jがローカルでしか使えないため検索画面までしか表示することができませんでした．もう少し，無料でNeo4jをオンラインで私用することができないかを調査していこうと思います．
[検索ページへ](https://searchonepieceknowledge.herokuapp.com/)


検索画面
![検索画面](https://github.com/kentaro123/search_onepiece_heroku/blob/master/sample_photo/%E6%A4%9C%E7%B4%A2%E7%94%BB%E9%9D%A2.png?raw=true)


検索結果
![検索結果](https://github.com/kentaro123/search_onepiece_heroku/blob/master/sample_photo/%E6%A4%9C%E7%B4%A2%E7%B5%90%E6%9E%9C.png?raw=true)

ナレッジグラフ
![ナレッジグラフ](https://github.com/kentaro123/search_onepiece_heroku/blob/master/sample_photo/%E3%83%8A%E3%83%AC%E3%83%83%E3%82%B8%E3%82%B0%E3%83%A9%E3%83%95.png?raw=true)

## システムの説明
* 検索したいワードを入力すると，その単語に関係のある悪魔の実の種類や人物名が表示される．（例）ゴムゴムの実→モンキー・D・ルフィ
* 検索したいワードの一部の入力でも検索することができる
* 複数存在するときは複数結果として表示される

## システムの内容
* Neo4jを用いてKnowledgeGraghとしてデータを保存してある
* 悪魔の実の種類 悪魔の実の名前　食べた人の名前　としてテキストに保存するとそこからKnowledgeGraghが構築される
* KnowledgeGraghは悪魔の実の種類→食べた人の名前としてつながっており，propertyに悪魔の実の名前が含まれている

## システムの利点
* 新しい悪魔の実の種類が出てきたときに，悪魔の実の種類 悪魔の実の名前　食べた人の名前　としてテキストファイルに入力するだけでOKなので，データの追加が簡単
* 検索したいワードの一部でも検索できるので曖昧な知識でも検索することができる

## ファイルの説明
* フォルダ：kg
<br>KnowledgeGraghを構築するためのプログラムが含まれている

* フォルダ：server
<br>Webアプリとして立ち上げるプログラムが含まれている

* フォルダ：data
<br>悪魔の実に関するデータが含まれている

* ファイル：conf.py
<br>Neo4jに接続する際の，ユーザ名やパスワードが含まれる

## 実行環境
* python 3.8.2
* Flask 1.1.2
* py2neo 3.2.0
* Neo4j 3.5.17

## 実行方法
* Neo4j 3.5.17をインストールしユーザ名とパスワードを設定する
* Neo4jを立ち上げる
* conf.pyのユーザ名，パスワードを変更
* kg/kg.pyを実行し，data/dataset.txt からKnowledgeGraghを構築
* server/run_server.pyを実行しWebアプリとして立ち上げる

## 作ってみた感想
インターンでKonledgeGraghを用いる機会があったので，その知識を利用して検索システムを作成してみました．KonledgeGragh特有の単語間の繋がりや，繋がりの向きをまだ上手に利用できていないので，そこをうまく活用できるシステムを考えていきたいと思いました．また，検索画面のデザインも今はまだシンプルなので使用者が心惹かれるようなデザインの勉強などもしてみたいと思いました．
