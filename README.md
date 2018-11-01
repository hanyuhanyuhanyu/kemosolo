# 関西ケモノサロンクローク管理システム

## 主たる機能

- ICカードリーダの疎通監視
- 各ゲート通過履歴の記録/参照
- [portal]にインスパイアされた見た目

[portal]:http://www.thinkwithportals.com/

## URL一覧

- / => メインゲートデジタルサイネージ用
- /watchdog => 管理者画面

## サーバ仕様

- 80番ポートのみ開放する

## API仕様

### ゲート管理

各ゲートの通過の記録および履歴参照を担う

##### GET => /api/gate

それまでのゲート通過履歴のうち最新100件を返す

##### GET => /api/gate/all

すべてのゲートのIPアドレスを返す

##### GET => /api/gate/history/(カードのID)

指定されたカードの通過履歴の最新5件を返す

##### POST => /api/gate/pass/master

総合ゲートを通過する際にリクエストを送る

###### ボディ部

|カラム|概要|
|:--:|:--:|
|card|カードのid|
|lane|レーンのIP|

##### POST => /api/gate/pass/slave/(laneのIPアドレス)

各レーンを通過する際にリクエストを送る

###### ボディ部

|カラム|概要|
|:--:|:--:|
|card|カードのid|


