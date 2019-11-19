### RustでSpotifyクライアントを作ってた(てる)話
----------------------
Shinjuku.rs #7 2019/11/19(@togatoga)
---
#### About Me
- togatoga
	- [Github: https://github.com/togatoga](https://github.com/togatoga)
	- [Twitter: https://twitter.com/togatoga](https://twitter.com/togatoga_)
- Rust LT#5
	- RustでゲームAIコンテスト出た話
---
#### Spotifyとは
- 音楽ストリーミング配信サイトの最大手の一つ(Apple Music, Amazon Music)
- 様々なプラットフォームでクライアントを提供している(Windows, macOS, Linux)
- Spotifyが提供しているWeb APIがかなり豊富
	- 公式のクライアント上でできることは大体APIが存在
		- [ドキュメント: https://developer.spotify.com/documentation/web-api/reference/](https://developer.spotify.com/documentation/web-api/reference/)
		- 一部機能はプレミアム会員のみ(曲の再生など)
			- 月額980円、学生なら480円
- SpotifyのAPIを使ってターミナルクライアントを作ってる話
---
#### モチベーション
- OS環境によって操作するキーバインドが若干異なる
	- ターミナルクライアントなら操作するキーバインドを統一(カスタマイズ)可能
- (仕事の逃避で)Rustを書きたかったから
	- 音楽を聞きながら仕事をするので普段使うものでなにか作りたかった
- Spotifyの公式クライアントの機能への不満
- ハッカー感でテンション上げる
---
#### Spoterm
- Spoterm
	- https://github.com/togatoga/spoterm
- 使用した主なライブラリ
	- UI
		- tui = "0.5"
		- termion = "1.5"
	- Spotify APIクライアント
		- rspotify = "0.7.0"
	- 並列ライブラリ
		- crossbeam = "0.7"

- Demo
---
#### 開発話
- コンパイルエラーとの挌闘
	- API側とUI側を分けるためにマルチスレッドとチャネルを導入
		- 所有権周りやチャンネルでコンパイルエラー
- GoやPythonに比べるとTUIやAPI(テキストUI)のライブラリが未熟
	- 日本語の表示がおかしくなる
	- 応用例などのブログ記事が少ない
- 他RustのOSSへのコントリビュート
	- rspotify
		- https://github.com/ramsayleung/rspotify/pull/48
		- https://github.com/ramsayleung/rspotify/pull/46
---
#### 今後の機能
- Spotifyの公式でできることは可能な限りサポート
	- アーティストのお気に入り
	- 曲の詳細表示
	- アルバム一覧
	- プレイリストの作成/削除/再生
- 自分が欲しい機能
	- Dislike機能(アーティストや曲のSkip機能)
	- 曲の再生回数
	- 1分モード
---
### 最後に
- 開発途中に後にspotify-tuiがリリース
	- https://github.com/Rigellute/spotify-tui
		- 現在Star数が3000超!!
			- 2019/08 ~
		- Spoterm
			- 2019/07 ~
- アイディアなどは寝かせずにすぐに実装しよう！！

