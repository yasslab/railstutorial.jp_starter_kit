# Windows 用のスターターキットツールを使った環境構築の手順

Windows でRailsチュートリアルを読み進めるための手順についてまとめています。

## 事前準備

Windowsでスターターキットを利用するためには以下のアプリケーションが必要です。

- [VirtualBox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp)をインストールする
- [Vagrant](https://www.vagrantup.com/downloads.html)をインストールする
- [Git for Windows](https://git-scm.com/download/win) をインストールする
- sshクライアント([TeraTerm](http://ttssh2.sourceforge.jp/)など)をインストールする


## Windows上で新規ユーザーを作成する

この項目は、Windowsのユーザー名に日本語が含まれている方向けのエラー回避作です。
Vagrantを実行する際、ユーザー名に日本語が含まれるとエラーが出るため、英語でアカウントを作成してください。(アカウント名が既に英語の場合は本項目をスキップしてください)

以下は、Windows 10 で新規ユーザーを作成する例です。

1.  Windowsボタンを押して人型のアイコンをクリックする。
2. 「アカウントの設定の変更」をクリック。
3.  左側にある「他のユーザ」をクリックし、「そのほかのユーザーをこのPCに追加」をクリック。
4. 「このユーザーのサインイン情報はありません」をクリック。
5. 「Microsoftアカウントを持たないユーザを追加」をクリック。
6.  「次へ」をクリック。入力例: 

> ユーザー名: ror
> パスワード: ror
> パスワードのヒント: ruby on rails

8.  Windowsボタンを押して人型のアイコンで先ほど作った、ユーザーを切り替えて下さい。

![Windowsアカウント](https://idobata.s3.amazonaws.com/uploads/attachment/image/952197/bc774979-cfb8-4e1e-b13f-39e03f2bd5e4/windows_ss.png)

## Vagrantでスターターキットツールを使えるようにする

※ 以下の手順は先ほど作ったユーザもしくは英字アカウントで行って下さい。

Windowsボタン右の検索マークを押し「PowerShell」と入力してPowerShellを左クリック、「別のユーザとして実行」をクリックする。

先ほど、入力したログイン情報を使って「OK」をクリックすると、PowerShellの入力画面が表示される

1. スターターキットを Gitからcloneする

次のコマンドを実行すると必要なキットが用意されます。

```
$ git clone https://github.com/yasslab/railstutorial.jp_starter_kit.git
```

2. `Vagrantfile` があるディレクトリに移動して、`vagrant up`を実行する

`cd`で移動した中に `Vagrantfile`があるので次のコマンドで実行する

```
$ cd /railstutorial.jp_starter_kit
$ vagrant up
```

3. TeraTermを起動し、`vagrant ssh`で出てきた設定情報をTeraTermに入力する。

> ホスト: 127.0.0.1
> TCPポート: 2222
> ユーザー名: vagrant
> パスワード: vagrant

4. `vagrant ssh` でゲストOSにログインする
```
$ vagrant ssh
```

5. `ruby --version` や `rails --version` でちゃんと動くか確かめる

無事に Ruby/Rails のバージョンが表示されれば環境構築は完了になります。お疲れ様でした :)
