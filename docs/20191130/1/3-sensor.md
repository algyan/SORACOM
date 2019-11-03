# 1-3: 絶対圧センサーのデータを SORACOM Harvest で可視化

絶対圧センサーのデータを SORACOM Harvest で可視化してみましょう

※センサーを組み合わせた開発を学びます

![ステップ3 ovewview](https://docs.google.com/drawings/d/e/2PACX-1vTWiU1rTH1oXMWIDuFoNhC6d0EJ3guDcLRi8jjTBFQEhoBvUaub9eQnkpX0eAKLwz9u78lWKVGccuD3/pub?w=480&h=360)

## 最初に. Wio LTE の電源を OFF にする

Wio LTE の microUSB ケーブルを抜き、電源を OFF にしてください

※いきなり抜いてOKです。また、すでに OFF になっている場合は次に進んでください

## 1. Wio LTE に絶対圧センサーを取り付ける

**※Wio LTE から microUSB ケーブルを抜いた状態にしてください**

Grove 絶対圧センサーを Wio LTE に取り付けます

Wio LTE の **I2C** に取り付けてください

![Wio LTE に絶対圧センサーを取り付けたところ](https://docs.google.com/drawings/d/e/2PACX-1vTZiJ7ep0q7IR2KoNJPnvHcTA_JMGEWTn5qwrlp8AC2YLAtETPRAGXss98LMKm061OlM76hDasUyIoS/pub?w=640&h=480)

<h2 id="sketch">2. スケッチを作成する</h2>

### 2-1. Arduino IDE を起動する

### 2-2. メニューの [ツール] で [ボード: "Seeed Wio LTE Cat.1"] と表示されていることを確認する

なっていなければ一覧から "Seeed Wio LTE Cat.1" を選んでください

### 2-3. GroveDriverPack ライブラリをインストールする

### TBD GroveDriverPack の説明

以下の URL より `Source code(zip)` を選択して zip ファイルをダウンロードします。
https://github.com/SeeedJP/GroveDriverPack/releases

Arduino IDE の [スケッチ] > [ライブラリをインクルード] > [.ZIP 形式のライブラリをインストール…] を選択し、先ほどダウンロードした `GroveDriverPack-1.4.0.zip` を探して「開く」をクリックすればインストール完了です
![](https://docs.google.com/drawings/d/e/2PACX-1vSyvtSl8JWQO_D5-pkwQsp0YVrrWOU76GlZohHURcIIEU-5W3PreVa9tCTUyYI94mId_y5zICWpC6xJ/pub?w=555&h=273)

### 2-4. スケッチをダウンロードする

Arduino IDE で [ファイル] > [新規ファイル] で新しいスケッチを開き、全て削除して何も書かれていない状態にします。

以下の URL を開き、表示されたスケッチをコピーして Arduino IDE にペーストします。
https://raw.githubusercontent.com/algyan/SORACOM/master/sketch/soracom-unified-omron_GroveDriverPack.ino

### 2-5. Wio LTE と PC を接続して DFUモード にする

### 2-6. 新しく開いたウィンドウの ![マイコンボードに書き込むアイコン](https://docs.google.com/drawings/d/e/2PACX-1vQiO83cFcX3LCXeioiTiaao57T4SGiIV6XZzcBP6poTwssCxmo7hLpoMh5qG3btyqgzs8Q-lAoE6Q0f/pub?w=100&h=100)(マイコンボードに書き込む) をクリック

### 2-7. 書き込みが完了したら、Wio LTE を 通常モードにする (RSTボタンを押せば通常モードになります)

通常モードで起動次第 SORACOM Harvest へデータを送信し始めます (電源投入から送信開始までは20~25秒程度かかります)

※標準では送信間隔が60秒です。早めたい場合は ステップ2 のやってみようを参考に `INTERVAL` を `5000` などに変えてください

## 3. 確認

SORACOM Harvest 上で温度(temp)・絶対圧(pres)が表示されるようになります  
※SORACOM Harvest の操作方法は ステップ2 で確認してください

![harvest-all-plot](https://docs.google.com/drawings/d/e/2PACX-1vSwebGsd_kOHhagej9sCP5WEVVYZt45KKKa_vgd343pLYyIMj95sFvdMtDtDSe3eixfDjJBizt3wlS5/pub?w=674&h=333)

## 4. Wio LTE の動作を止める

止める方法は Wio LTE の電源を OFF (= microUSBケーブルを抜く) してください

## 以上で本章は終了です

達成状況を運営表へご記入ください。

* [2-1.クラウド連携 / Azure IoT Central 編](../2/1-soracom-beam+azure-iot-central.md) に進んで下さい
* [目次ページへ戻る](../index)

## うまく動かなかったら（トラブルシュート）

**Wio LTE を通常モードで動かして1分経ってもデータが表示されない**

* 原因: 電波状況などによりセルラー通信に失敗している
* 対策: RST ボタンを押して Wio LTE を再度起動しなおしてください

**SORACOM Harvest でデータ表示がされない**

* 原因: ステップ2 で行った稼働時間のデータが原因で、データのY軸が大きすぎて表示されない場合があります
* 対策: SORACOM Harvest 上で下記操作を行ってください
    - 凡例をクリックすることで当該のデータを非表示できる機能
    - 他の形式で表示する機能
    - 最大値/最小値の設定ができる機能

![harvest-exclude-plot](https://docs.google.com/drawings/d/e/2PACX-1vRa8wgI9GtmrCNPLiKhwF6o-tkCTg4QBC3xUBY_nxK3urV4B0r0b5yEsSLWjIy88tJJKAwCQYJVcvGm/pub?w=634&h=300)

![harvest-alt-plot](https://docs.google.com/drawings/d/e/2PACX-1vR_nFPgaTosGb5Ywy0KsNp6d7yP1MHkMcM6uUqT8fuw4WMdsSTn3fct1izl6MjEmeWLDq6yi3_5lnwW/pub?w=731&h=306)
