## [RADIO SORT](https://radio-sort.xyz/)
##### ドラッグ&ドロップでラジオ番組に順位をつけるアプリ https://radio-sort.xyz/

<img src="https://user-images.githubusercontent.com/53632056/83470954-639a0080-a4be-11ea-9ab7-ca54cae263c0.gif" width="30%">
<img src="https://user-images.githubusercontent.com/53632056/83470938-5d0b8900-a4be-11ea-8495-1df7e60e7ded.png" width="30%">
<img src="https://user-images.githubusercontent.com/53632056/83470947-6137a680-a4be-11ea-9290-b50d57db6079.png" width="30%">
<img src="" width="30%">

## 機能
|  |  |
|:---:|:---:|
|ドラッグ&ドロップ | 画像左|
|放送局別週間番組表 | 画像右|
|ラジオ人気ランキング |画像真中|
|twitter認証ログイン | omniauth-twitter使用|
|tweet投稿 |twitterログイン時のみ |
|ラジオ検索 |番組・パーソナリティ・放送局から検索 |
|ユーザー検索 |性別・年代・好きな番組から検索 |
|ランキングの絞り込み |ユーザーの性別、年代・放送局から絞り込み |
|コメントCRUD |ラジオ詳細ページに投稿(AJAX) |

## なぜこのアプリを作成したのか
[・ラジオ情報を取得できるapiが公開されていた](https://ststarfield.blog.fc2.com/blog-entry-150.html)

[・ドラッグ&ドロップで順位を着けて保存する実装が公開されていた](https://qiita.com/jnchito/items/391fb16d3f69fda9bdae)

オリジナリティを発揮できるテーマと機能を調査し、上記の２点が決め手となった。

### ソートをテーマにした理由
twitterで、#○○ソートというタグを偶に見かけていた。

それは、主にアイドルグループの中で誰が一番好きかを表明するためのタグだった。

年末にはこぞって、”年間ベスト○○”といったtweetが各ジャンルで投稿される。

好きなジャンルについて、自分だけの順位をつけることに需要があると判断した。

## クラウド
image

## 要件定義

| gem | usage |
|:---:|:---:|
| [カタログ設計](https://drive.google.com/file/d/18su-bFDk2lm78DGGrAocKHfuGbI8KyJw/view) |[テーブル定義](https://drive.google.com/open?id=14TFr-lGAmlESY14Kn3y8R-7Zqiitp3eo) |
|[ワイヤーフレーム](https://drive.google.com/open?id=1g-u-8UI5Wyv6E817qPA5uoZZWSi0TY0j) |[ER図](https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png) |
|[ER図](https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png) | [画面遷移図](https://user-images.githubusercontent.com/53632056/76596050-91674d00-6540-11ea-9e0c-0d6e77469a85.png)|
|<img src="https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png" width="50%"> |<img src="https://user-images.githubusercontent.com/53632056/76596050-91674d00-6540-11ea-9e0c-0d6e77469a85.png" width="50%"> |


##### [カタログ設計](https://drive.google.com/file/d/18su-bFDk2lm78DGGrAocKHfuGbI8KyJw/view)
##### [テーブル定義](https://drive.google.com/open?id=14TFr-lGAmlESY14Kn3y8R-7Zqiitp3eo)
##### [ワイヤーフレーム](https://drive.google.com/open?id=1g-u-8UI5Wyv6E817qPA5uoZZWSi0TY0j)
##### [ER図](https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png)
##### [画面遷移図](https://user-images.githubusercontent.com/53632056/76596050-91674d00-6540-11ea-9e0c-0d6e77469a85.png)
 
<img src="https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png" width="40%">
<img src="https://user-images.githubusercontent.com/53632056/76596050-91674d00-6540-11ea-9e0c-0d6e77469a85.png" width="40%">

## 使用gem
| gem | usage |
|:---:|:---:|
|ranked-model |お気に入りに順位を与える |
|jquery-ui-rails |順位をドラッグ&ドロップでつける |
|slim-rails |viewファイルをslimに変換 |
|materialize-sass |CSSフレームワーク |
|ransack |ラジオ検索・ユーザー検索 |
|devise |ログイン機能(twitter認証) |
|nokogiri |apiから取得したxmlをパース |
|kaminari |radikoAPIからデータをパース |
|omniauth-twitter |twitterログイン |
|twitter |twitter投稿 |
|rubocop-rails |コードの静的解析 |
|rspec-rails |テスト |
  
## バージョン
ruby '2.6.5'

Rails '5.2.4.1'

PostgreSQL '11.5'

## 作者
##### [wantedly](https://www.wantedly.com/users/113160879)
##### [qiita](https://qiita.com/takayuki-takahashi-dic)
##### [github profile](https://github.com/tktkaws)