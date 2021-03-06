# おうちネットワーク

ホスト名から出てるリンクは、ブラウザでリンク開けて嬉しそうなサービスを適当に一つ。
[これ](https://gist.github.com/nna774/c28c8c908a9feea4e44d)とかも参照のこと(ちょっと古い)。

## 10.42.42.0/24

外向きのものを置く DMZ ゾーン。
内向きへの通信は制限されている。

`10.42.42.3 -> 10.8.8.33/22 TCP` のみが通るらしい。

これ書いていいのかと思ったけど、[nna774/yukari](https://github.com/nna774/yukari/) がもう公開されてるから同じか。

`yui` が内向き DNS を担当していて、家の中に移したい。

### 割り当て状況

|hostname|ip|名前の由来|
|---|---|---|
|yukari|10.42.42.1|家の中と外を分ける八雲紫|
|[yui](https://yui.nna774.net/)|10.42.42.3|櫟井唯|

## 10.8.8.0/24

内向き

`yukari` がルーティングと DHCP をやっている。
`yui` を DNS として、自分を NTP として配ってる。
`akashi` と `ichigo` と `mba` は DHCP fix assign してる。

### 割り当てポリシー

|Range|役割|
|---|---|
|10.8.8.1-10|予約|
|10.8.8.11-31|インフラ|
|10.8.8.32/27|サーバ|
|10.8.8.64/26|空き|
|10.8.8.128/26|DHCP|

### 割り当て状況

|hostname|ip|名前の由来|
|---|---|---|
|droid(退役)|10.8.8.11|Android OS から(Android が動いていたわけではない)|
|[yukari](http://yukari.nna774.net/)|10.8.8.12|日向縁ではない|
|[akashi](https://akashi.nna774.net/)|10.8.8.13|明石(艦これ) と明石さん(四畳半神話大系) が6:4 ぐらい|
|kaede|10.8.8.14|高垣さん|
|[ichigo](http://ichigo.nna774.net/)|10.8.8.15|星宮いちご|
|nonohara|10.8.8.16|||
|[utsutsu](http://utsutsu.nna774.net/)|10.8.8.32|ガッチャマンクラウズのうつつ(元々はVMホストであった)|
|[sazanami](http://sazanami.nna774.net:8000)|10.8.8.33|漣(艦これ)|
|[deneb](https://10.8.8.34/)|10.8.8.34|？(先輩のところからうちに居候中)|
|ushio|10.8.8.35|amatsukazeからrenamed|
|yumemi|10.8.8.36|sendaiよりrename|
|sumi|10.8.8.37||
|mba|10.8.8.142|MacBookAir|
