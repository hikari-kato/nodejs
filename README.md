# 👻 Node.jsは怖くないよ
改めてNode.jsについてまとめてみました。  
少し楽にフロントエンドの開発をしたいと思うと、今では避けて通れないのが「[Node.js](https://nodejs.org/ja/about/)」です。  
少しとっつきづらそうですが、実際に使用しなくても少し知っておくだけで今後説明するツールをスムーズに理解するのに役立ちます。

## Node.jsってなんだろう？
サーバーサイド（普段使ってるPHPとか）で動くJavaScriptです。  
動作が軽量なため主にリアルタイム性の高いWebサービス（動画配信やチャット）やアプリなどで使用されることが多いようです。

Webサイトの開発では、JSファイルをまとめるモジュールバンドラーと呼ばれる「[webpack](https://webpack.js.org/)」やさまざまなタスクをプログラム処理で自動化してくれるタスクランナーと呼ばれる「[Gulp](https://gulpjs.com/)」や「[Grunt](https://gruntjs.com/)」がよく使われています。  
これらはNode.jsをベースに作られています。

## とりあえずインストールしてみよう！
最近は[Homebrew](https://brew.sh/index_ja.html)というMac用のパッケージマネージャーで管理するのが一般的です。  
すでに何かの機会にインストールしている場合もあるかもしれませんので、バージョンを確認してみましょう。

以下ターミナルを起動して打ち込む。
~~~
brew -v
~~~

古いバージョンだったらアップデートしましょう。
~~~
brew update
~~~

バージョンが表示されていれば使っているPCにすでに入っています。  
入っていないようであれば[公式サイト](https://brew.sh/index_ja.html)のトップにあるスクリプトをコピーしターミナルにペーストして動かしてみてください。

もう一つNode.jsのバージョンを管理するためのツール[nodebrew](https://github.com/hokaccha/nodebrew)も入れてみましょう。  
プロジェクトのNode.jsのバージョンによって切り替えたりなどするのに便利です。  
~~~
brew install nodebrew
~~~

インストールされたかバージョンも確認しておきましょう。  
問題なくバージョンが表示されれば下準備は完了です。
~~~
nodebrew -v
~~~

ではNode.jsをインストールします。  
特に目的がなければ下記のコマンドで最新版を入れておきましょう。
~~~
nodebrew install latest
~~~

指定のバージョンを入れたい場合は末尾を変更します。  
下のコマンドでは「v14.4.0」をインストールしています。（必要に応じて変更してください）
~~~
nodebrew install v14.4.0
~~~

下記のコマンドではnodebrewでインストールしたバージョンが一覧で見れます。
~~~
nodebrew ls
~~~

実行結果
~~~
v14.4.0

current: none
~~~

どのバージョンを使うか下記のコマンドで設定します。  
下のコマンドでは「v14.4.0」を指定しています。（必要に応じて変更してください）
~~~
nodebrew use v14.4.0
~~~

もう一度下記のコマンドでインストール一覧を確認してみましょう。
~~~
nodebrew ls
~~~

実行結果
~~~
v14.4.0

current: v14.4.0
~~~

currentにバージョンが表示されていれば大丈夫です◎  

## 設定ファイルを編集しよう
最後にシェルの設定ファイルにパスを追加（PATHを通す）します。  
シェルの種類によって設定するファイルが違うので、下のイメージを参考にまずは「bash」か「zsh」か確認してみましょう。  

イメージでは「zsh」ですが、Macのデフォルトである「bash」の説明を先にします。  
CatalinaからMacではzshを推奨するようになりました。  
今回は割愛しますが、興味があればzshも使ってみましょう。

![ターミナル説明_01](https://user-images.githubusercontent.com/32893962/85084284-4fb90300-b20f-11ea-87af-0cbbdbf9c84f.png)

### bashの場合
まずはホームディレクトリの下に設定ファイルである「.bashrc」があるか下記のコマンドで確認します。  
最初のコマンドでホームディレクトリに移動して、次のコマンドで一覧を表示しています。  
lsは末尾に-aを付けると隠しファイルも表示することができます。
~~~
cd
~~~

~~~
ls -a
~~~

「.bashrc」ファイルが見つからない場合は作成します。
下記のコマンドで作成しましょう。  
すでにファイルがある場合は下記のコマンドは不要です。
~~~
touch .bashrc
~~~

「.bashrc」ファイルにパスを追加します。
~~~
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bashrc
~~~

設定ファイルの変更を反映します。
~~~
source ~/.bashrc
~~~

最後にnodebrewのnodeが使えることを確認して終了です。  
おつかれさまでした！
~~~
node -v
~~~

### zshの場合
まずはホームディレクトリの下に設定ファイルである「.zshrc」があるか下記のコマンドで確認します。  
基本は上のbashと同じですが設定ファイルが違う所にだけ注意しましょう。  
最初のコマンドでホームディレクトリに移動して、次のコマンドで一覧を表示しています。  
lsは末尾に-aを付けると隠しファイルも表示することができます。
~~~
cd
~~~

~~~
ls -a
~~~

「.zshrc」ファイルが見つからない場合は作成します。
下記のコマンドで作成しましょう。
~~~
touch .zshrc
~~~

「.zshrc」ファイルにパスを追加します。
~~~
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
~~~

設定ファイルの変更を反映します。
~~~
source ~/.zshrc
~~~

最後にnodebrewのnodeが使えることを確認して終了です。  
おつかれさまでした！
~~~
node -v
~~~