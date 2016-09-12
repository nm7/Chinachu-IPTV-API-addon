# Chinachu-IPTV-API-addon (modified version)
upstream の Chinachu-IPTV-API-addon に、Chinachu の watch-channel API を利用して
リアルタイムエンコードした放送を受信できるチャンネルプレイリストを生成する機能を
追加したものです。

upstream の Chinachu-IPTV-API-addon は DEPRECATED になっており、Chinachu の watch-channel API も
次期バージョンである Chinachu Air ではなくなるそうなので注意。


# インストール
resource-iptv.json と script-iptv.vm.js の 2つを、Chinachu の api ディレクトリに置いてください。


# 使い方

* `GET /api/iptv/epg.xml`

 * XMLTV フォーマットの EPG を返します。

* `GET /api/iptv/channel.m3u8(?quality=(ultrahigh|high|middle|low))`

 * M3U8 フォーマットのチャンネルプレイリストを返します。
quality パラメータを引数に与えない場合は、オリジナルのチャンネルストリームが受信できるリストを返します (upstream と同じ挙動)。

 * quality パラメータを引数に与えた場合は、各々に応じたサイズ・ビットレートの H.264 + AAC にエンコードし、MPEG2-TS コンテナに
格納したチャンネルストリームが受信できるリストを返します。

 * サイズ・ビットレートは script-iptv.vm.js の冒頭でハードコードしているので、必要に応じて変更してください。


# IPTV アプリ
iOS、Android に GSE IPTV というアプリをインストールして、EPG とリモートプレイリストに上記 URL をいれると、いい感じのリアルタイムテレビ視聴アプリになります。

* iOS 版
 * https://itunes.apple.com/jp/app/gse-smart-iptv-pro/id1028734023

* Android 版
 * https://play.google.com/store/apps/details?id=com.gsetech.smartiptv


# License
upstream と同じ、GPL v2 です。
