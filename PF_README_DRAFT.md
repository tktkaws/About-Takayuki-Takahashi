## [RADIO SORT](https://radio-sort.xyz/)
https://radio-sort.xyz/

ラジオ番組にドラッグ&ドロップで順位を着けるアプリ

![TOPページ](https://user-images.githubusercontent.com/53632056/83470951-63016a00-a4be-11ea-815a-b713d1145a36.png)

<img src="https://user-images.githubusercontent.com/53632056/83470951-63016a00-a4be-11ea-815a-b713d1145a36.png" width="300x300">
<img src="https://user-images.githubusercontent.com/53632056/83470951-63016a00-a4be-11ea-815a-b713d1145a36.png" width="200x200">
<img src="https://user-images.githubusercontent.com/53632056/83470951-63016a00-a4be-11ea-815a-b713d1145a36.png" width="100x100">


## 機能
#### ドラッグ&ドロップ(AJAX)
![ドラッグ&ドロップ](https://user-images.githubusercontent.com/53632056/83470954-639a0080-a4be-11ea-9ab7-ca54cae263c0.gif)
#### 放送局別週間番組表
![放送局別週間番組表](https://user-images.githubusercontent.com/53632056/83470947-6137a680-a4be-11ea-9290-b50d57db6079.png)
#### ラジオ人気ランキング
ランキングはユーザーが着けた順位にpointを付与し、それを集計
1位＝10pt、2位＝8pt、〜〜〜6位以降は1pt

![ランキングの絞り込み](https://user-images.githubusercontent.com/53632056/83470938-5d0b8900-a4be-11ea-8495-1df7e60e7ded.png)

#### その他の機能
twitter認証ログイン
tweet投稿(twitterログイン時)
ラジオ検索	番組・パーソナリティ・放送局から検索
ユーザー検索	性別・年代・好きな番組から検索
ランキングの絞り込み ユーザーの性別、年代・放送局から集計対象を絞り込み
ユーザーフォロー
コメントCRUD ラジオ詳細ページに投稿(AJAX)

## なぜこのアプリを作成したのか
[・ラジオ情報を取得できるapiが公開されていた](https://ststarfield.blog.fc2.com/blog-entry-150.html)

[・ドラッグ&ドロップで順位を着けて保存する実装が公開されていた](https://qiita.com/jnchito/items/391fb16d3f69fda9bdae)

オリジナリティを発揮できるテーマと機能を調査し、上記の２点が決め手となった。

### ソートをテーマにした理由
twitterで、#○○ソートというタグを偶に見かけていた。

それは、主にアイドルグループの中で私は誰が一番好きなのかを表明するためのタグだった。

年末にはこぞって、”年間ベスト10”といったtweetが各ジャンルで投稿される。

好きなジャンルについて、自分だけの順位を作成することはとても楽しい。

順位づけ(ソート)というテーマに需要があると判断した。

## クラウド
image

## 要件定義
##### [カタログ設計](https://drive.google.com/file/d/18su-bFDk2lm78DGGrAocKHfuGbI8KyJw/view)
##### [テーブル定義](https://drive.google.com/open?id=14TFr-lGAmlESY14Kn3y8R-7Zqiitp3eo)
##### [ワイヤーフレーム](https://drive.google.com/open?id=1g-u-8UI5Wyv6E817qPA5uoZZWSi0TY0j)
##### ![ER図](https://user-images.githubusercontent.com/53632056/72213365-42496f80-3531-11ea-8d37-742a78e9961d.png) 
##### ![画面遷移図](https://user-images.githubusercontent.com/53632056/76596050-91674d00-6540-11ea-9e0c-0d6e77469a85.png)

## 使用gem
| gem | usage |
|:---:|:---:|
|ranked-model |お気に入りに順位を与える |
|jquery-ui-rails |順位をドラッグ&ドロップでつける |
|slim-rails |viewファイルをslimに変換 |
|materialize-sass |CSSフレームワーク |
|ransack |ラジオ検索・ユーザー検索 |
|devise |ログイン機能(twitter認証) |
|nokogiri |radikoAPIからデータをパース |
|nokogiri |radikoAPIからデータをパース |
|nokogiri |radikoAPIからデータをパース |
|nokogiri |radikoAPIからデータをパース |
|nokogiri |radikoAPIからデータをパース |
|nokogiri |radikoAPIからデータをパース |
kaminari
omniauth-twitter
twitter
faker
gem 'rspec-rails'
  gem 'rspec_junit_formatter'
  gem 'rubocop'
  gem 'rubocop-rails'
  
## バージョン情報
ruby '2.6.5'

Rails '5.2.4.1'

PostgreSQL '11.5'

## author
wantedly
qiita
profile　github
