# Railsチュートリアル スターターキット

本ツールは、Railsチュートリアルの環境構築がうまくいかない人向けの救済ツールです。

HerokuやGitHubのセットアップは各自でやる必要がありますが(やや難しいかもしれません)、
Ruby/Railsを使った開発はすぐにできるようにセットアップされています :)

```
※ なお、HerokuやGitHubの項目は飛ばしてしまっても次に進めるように構成されているので、
　「環境構築がうまくいかないけど、まずは１週通してみたい」といったときに便利です。
```

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

1. [VirtualBox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp)をインストールする
2. [Vagrant](https://www.vagrantup.com/downloads.html)をインストールする
3. Windowsの場合: 英字のローカルアカウントを作る (`ror`など)
4. Windowsの場合: sshクライアント([TeraTerm](http://ttssh2.sourceforge.jp/)など)をインストールする
5. `Vagrantfile` があるディレクトリに移動して、`vagrant up`を実行する
6. `vagrant ssh` でゲストOSにログインする
7. `ruby --version` や `rails --version` でちゃんと動くか確かめる


### 動作確認

もしちゃんと開発できるか不安であれば、
`vagrant ssh`でログインしたあと、
次のコマンドを１行ずつ打っていって動作確認することもできます。
(`#`から始まる行はコメントです。打たなくても問題ありません。)

```sh
git clone https://github.com/yasslab/sample_apps.git
cd sample_apps/ch11
bundle install
bundle exec rake db:migrate
bundle exec rake db:populate
bundle exec rake db:test:prepare

# テストが通ることを確認する
bundle exec rspec

# rails server が立ち上がるか確認する
bundle exec rails server

# ホストOS (お手持ちのパソコン) のブラウザを立ち上げ、
# アドレズバーに http://localhost:3000/ を打ち込んで画面が開くか確認する
```

### 注意点

公開鍵の登録や暗号鍵の登録が少し難しいので、
HerokuへのデプロイやGitHubへのpushは少し難しいかもしれません :(

とはいえ、Railsチュートリアルの開発において支障は無いので、
本ツールを使って開発を進める場合は、HerokuへのデプロイやGitHubへのpushは飛ばしてお読みください.   
(２週目で、ぜひ自分のPCへの環境構築にトライしてみてください!)


## 最後に

Railsチュートリアルの環境構築が難しくてうまくいかなかったときなどに、本ツールをご活用ください :)   
本ツールが読者のお役に立っていれば幸いです.

ヤスラボ チーム一同
http://yasslab.jp/




### おまけ

今回のゲストOSでは次のスクリプトを実行して作成されています。
もし興味があれば、覗いてみてもよいかもしれません :)

ゲストOSの構築スクリプト
https://github.com/hanachin/railstutorial_box/blob/master/bootstrap.sh


