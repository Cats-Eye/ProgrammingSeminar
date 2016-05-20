# bootstrapとは
既にある程度完成したcssのフレームワークが用意されているので、ちょっとの手間で簡単に見栄えの良いwebページを作ることができる！もともとはTwitter社内で作られたもので以前はTwitter Bootstrapと呼ばれていた。

# ダウンロード
まずは[ここ](http://getbootstrap.com/ "Bootstrap")で「Download Bootstrap」をクリック。ダウンロードページへとんだら、「Download Bootstrap」からダウンロード。またダウンロードページの下のほうにHTMLのサンプルコードがあるのでこれをsample.htmlとしてダウンロードしたbootstrapフォルダ内に保存。sample.htmlをブラウザで開くとHello,world!と表示されるか確認。準備はこれで完了。以下に注釈をつけたsample.htmlも用意した。

```html:sample.html
<!DOCTYPE html>
<!-- ドキュメント言語コードを指定 -->
<html lang="ja">

  <head>
    <!-- 文字のエンコーディング指定 -->
    <meta charset="utf-8">
    <!-- InternetExplorerのブラウザではバージョンによって崩れることがあるので、互換表示をさせないために設定するmetaタグ -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- BootstrapのCSS読み込み(レスポンシブWebデザインを使うために必要なmetaタグ) -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- ブラウザのツールバーに表示されるやつ、省略不可 -->
    <title>Bootstrap Sample</title>
    <!-- BootstrapのCSS読み込み -->
    <link href="css/bootstrap.min.css" rel="stylesheet">
    <!-- JavaScriptより先にjQuery読み込み -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <!-- BootstrapのJS読み込み -->
    <script src="js/bootstrap.min.js"></script>
  </head>

  <body>
    <h1>Hello, world!</h1>
  </body>s

</html>
```

# ボタン
Bootstrapを使うと簡単にボタンにスタイルをつけられる。class="btn btn-xxx"のxxxを書き換えることでスタイルを変えられる。またclass="btn btn-primary btn-xxx"のxxxを書き換えることでボタンのサイズを変更できる。サイズは指定しなければdefaultのサイズになる。

```html:sample1.html
<button type="button" class="btn btn-default">Default</button><!-- default 白地に黒文字 -->
<button type="button" class="btn btn-primary">Primary</button><!-- primary 青地に白文字 -->
<button type="button" class="btn btn-success">Success</button><!-- success 緑地に白文字 -->
<button type="button" class="btn btn-info">Info</button><!-- info 水色地に白文字 -->
<button type="button" class="btn btn-warning">Warning</button><!-- warning オレンジ地に白文字 -->
<button type="button" class="btn btn-danger">Danger</button><!-- danger 赤地に白文字 -->
<button type="button" class="btn btn-link">Link</button><!-- link 白地に青文字 -->

<button type="button" class="btn btn-primary btn-lg">Large button</button>
<button type="button" class="btn btn-primary">Default button</button>
<button type="button" class="btn btn-primary btn-sm">Small button</button>
<button type="button" class="btn btn-primary btn-xs">Extra small button</button>
```

# グリッドシステム
このシステムのおかげでレスポンシブデザイン(様々な種類の機器や画面サイズに単一のファイルで対応すること)を手軽に実装できる。Bootstrapでは以下４種類の画面サイズを想定している。

| 名称 | デバイス |
|:-----------|:------------|
|Exstra small(xs)|スマートフォンなど768px未満|
|Small(sm)|タブレット768~991px|
|Medium(md)|中型ディスプレイ992~1199px|
|Large(lg)|大型ディスプレイ1200px以上|

Bootstrapではコンテナのなかに要素を記述する。コンテナにはcontainer（固定幅）とcontainer-fluid（流動幅）の２種類がある。containerは固定幅だがレスポンシブで表示領域に収まらなければ幅を狭める。スマートフォンサイズ(768px未満)の場合は全幅、タブレットサイズ(768～991px)の場合は750px固定、中型ディスプレイ(992～1199px)の場合は970px固定、大型ディスプレイ(1200px以上)の場合は1170px固定となる。コンテナはセンタリングされ、左右には15pxのパディング(余白)が付く。それに対しcontainer-fluidは画面サイズに合わせて流動的に画面にフィットし、表示領域の幅全体に表示する。768px以下ではcontainer（固定幅）もcontainer-fluid（流動幅）も違いがない。

Bootstrapではコンテナを12個のグリッドに分割してそれをカラムに割り当てることでレイアウトを制御する。例えば以下のコードだと2:6:2:2。カラムの合計が12を超える場合は複数行で表示される。

```html:sample2.html
<div class="container-fluid">
  <div class="row">
    <div class="col-xs-2 bg-info">col-xs-2</div>
    <div class="col-xs-6 bg-success">col-xs-6</div>
    <div class="col-xs-2 bg-warning">col-xs-2</div>
    <div class="col-xs-2 bg-danger">col-xs-2</div>
  </div>
</div>
```

col-xs-xを使用した場合、カラムは常に横に並ぶ。col-sm-xを使用すると、タブレットサイズ(768px)以上の画面では横並び、それ未満では縦並び。col-md-xを使用すると、中型ディスプレイサイズ(992px)以上で横並び、それ未満で縦並び。col-lg-xを使用すると、大型ディスプレイサイズ(1200px)以上で横並び、それ未満で縦並び。画面サイズに応じて比率を変更することも可能。つまりブレイクポイントは３つある。以下のコードだとスマートフォンサイズでは3:3:3:3、タブレットサイズでは6:2:2:2、中型ディスプレイでは2:2:2:6の割合で分割する。

```html:sample3.html
<div class="container-fluid">
  <div class="row">
    <div class="col-xs-3 col-sm-6 col-md-2 bg-info"> </div>
    <div class="col-xs-3 col-sm-2 col-md-2 bg-success"> </div>
    <div class="col-xs-3 col-sm-2 col-md-2 bg-warning"> </div>
    <div class="col-xs-3 col-sm-2 col-md-6 bg-danger"> </div>
  </div>
</div>
```

またブレイクポイントごとに表示非表示を切り替えることもできる。

```html:sample4.html
<div class="container-fluid">
  <div class="row">
    <div class="col-xs-2 bg-info">col-xs-2</div>
    <div class="col-xs-8 visible-md bg-primary">col-xs-8 visible-md</div>
    <div class="col-xs-8 hidden-sm bg-success">col-xs-8 hidden-sm</div>
    <div class="col-xs-2 bg-warning">col-xs-2</div>
  </div>
</div>
```


# 参考
[Bootstrap使い方超入門](http://www.atmarkit.co.jp/ait/articles/1403/19/news034.html)

[とほほのBootstrap入門](http://www.tohoho-web.com/ex/bootstrap.html)
