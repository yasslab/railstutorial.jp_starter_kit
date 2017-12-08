# Railsチュートリアル スターターキット

本ツールは、仮想環境 (VirtualBox + Vagrant) を使って[Railsチュートリアル](https://railstutorial.jp)の環境構築をするためのものです。Railsの環境構築にお困りの場合は試してみてください :)

なお、RailsチュートリアルではHeroku/BitBucket/GitHubの項目をスキップしても次に進めるように構成されています。このため、Railsの開発環境さえ整えばRailsチュートリアルを最後まで読み進めることが可能です。

## ファイル構成

### `Vagrantfile` ファイル

ゲストOS (もう一つのパソコンだと思ってください) をダウンロードするための必要な設定が書かれています。
`ls` コマンドで Vagrant ファイルが見える位置 (ディレクトリ) まで移動して `vagrant up` と実行するだけで
Railsチュートリアルが始められる環境が整います (Windows 8 / Mac OS X 10.10 / Ubuntu 14.04 にて確認済み)。

### `data` ディレクトリ

`data`ディレクトリは、Vagrant というツールを使って立ち上げた
ゲストOSの `/vagrant` ディレクトリと同期しています。

ホストOS (お手持ちのパソコン) に Sublime Text などのエディタをインストールし、
`data` 以下にあるファイルを操作することで、ゲストOS上のファイルを操作することができます。

これにより、ゲストOSの中でRailsアプリを立ち上げ、コーディングや編集、
ブラウザでの確認(※)をホストOSで行う、といった開発が可能になります。

```
※ ゲストOS上で`rails server` を立ち上げると、
　Vagrant のポートフォワーディングという機能が働き、
　ホストOSの localhost:3000 というURLからRailsのアプリケーションを確認することができます。
```

## 本ツールを使った環境構築の手順

まずは下記リンクからスターターキットをダウンロードし、Zip ファイルを展開します。   
https://github.com/yasslab/railstutorial.jp_starter_kit/archive/master.zip


###  Mac/Linuxの場合
1. [VirtualBox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp)をインストールする
2. [Vagrant](https://www.vagrantup.com/downloads.html)をインストールする
5. `Vagrantfile` があるディレクトリに移動して、`vagrant up`を実行する
6. `vagrant ssh` でゲストOSにログインする
7. `ruby --version` や `rails --version` でちゃんと動くか確かめる

### Windowsの場合

下記の手順にしたがってスターターキットを利用することができます。   
https://github.com/yasslab/railstutorial.jp_starter_kit/blob/master/for_windows.md

### 動作確認

もしちゃんと開発できるか不安であれば、
`vagrant ssh`でログインしたあと、
次のコマンドを１行ずつ打っていって動作確認することもできます。
(`#`から始まる行はコメントです。打たなくても問題ありません。)

```sh
git clone https://github.com/yasslab/sample_apps.git
cd sample_apps/5_1_2/ch14
bundle install
rails db:migrate

# テストが通ることを確認する
rails test

# rails server が立ち上がるか確認する
rails server

# ホストOS (お手持ちのパソコン) のブラウザを立ち上げ、
# アドレズバーに http://localhost:3000/ を打ち込んで画面が開くか確認する
```

### 特定のRailsバージョンを使う

Railsには様々なバージョンがあります。`vagrant ssh`でログインしたあと、次のコマンドを１行ずつ打っていって、特定のバージョンのRailsを使えるようにできます。

今回は`Rails 5.1.2`をインストールしてみましょう。
1. `$ rbenv install 2.3.0`
2. `$ rbenv global 2.3.0`
3. `$ gem install rails -v '5.1.2'`
4. `$ ruby --version` や `rails --version` などでちゃんと指定したバージョンになっているか確認してください。

### 注意点

公開鍵の登録や暗号鍵の登録が少し難しいので、
HerokuへのデプロイやGitHubへのpushは少し難しいかもしれません :(

とはいえ、Railsチュートリアルの開発において支障は無いので、
本ツールを使って開発を進める場合は、HerokuへのデプロイやGitHubへのpushは飛ばしてお読みください。(２週目では、ぜひ自分のPCへの環境構築にもトライしてみてください!)


## 最後に

Railsチュートリアルの環境構築が難しくてうまくいかなかったときなどに、本ツールをご活用ください。
本ツールが読者のお役に立っていれば幸いです.

YassLab チーム一同    
https://yasslab.jp/


## 関連リポジトリ/リンク

- [yasslab/sample_apps](https://github.com/yasslab/sample_apps)
- [yasslab/railstutorial.jp](https://github.com/yasslab/railstutorial.jp)
- [Rails チュートリアル](https://railstutorial.jp)
- [Rails 解説動画](https://railstutorial.jp/#screencast)
- [Rails ガイド](https://railsguides.jp)


## ライセンス

The MIT License (MIT)

Copyright &copy; 2015-2017 [YassLab](https://yasslab.jp)

![YassLab Logo](https://yasslab.jp/img/logo_800x200.png)
