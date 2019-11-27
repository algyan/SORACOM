# 1-3.絶対圧センサーのデータを SORACOM Harvest で可視化

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

![Wio LTE に絶対圧センサーを取り付けたところ](https://docs.google.com/drawings/d/e/2PACX-1vRBi2zlLImt0IEXEjmQlSRzZJdPagnI5K_UmLCJatwcNM95GCieWVogoqlJucfslloCoj9_myL9ICdi/pub?w=527&h=494)

<h2 id="sketch">2. スケッチを作成する</h2>

### 2-1. Arduino IDE を起動する

### 2-2. メニューの [ツール] で [ボード: "Seeed Wio LTE Cat.1"] と表示されていることを確認する

なっていなければ一覧から "Seeed Wio LTE Cat.1" を選んでください

### 2-3. GroveDriverPack ライブラリをインストールする

Seeed 社から、Grove モジュールを Wio LTE ですばやく利用するためのライブラリ「GroveDriverPack」が提供されているので、これを使えるようにしましょう

Arduino IDE の [スケッチ] > [ライブラリをインクルード] > [ライブラリを管理...] を選択し、検索窓にて「GroveDriverPack」と入力しの「インストール」をクリックすればインストール完了です

![manageLibrary](https://docs.google.com/drawings/d/e/2PACX-1vQJ_BtRf8Hd_iFNjt9tIuuDrJY0x6z_-7yiBtl8Ny-N65HxskBRSlY-6iWyxP1et_0oAh2KBotxWvhN/pub?w=462&h=126)

![installGroveDriverPack](https://docs.google.com/drawings/d/e/2PACX-1vQFmGnB-8T70rc-gFmzuqRpQQ8VPYZtVEYVrdScJG7F2pWWm8oNhuret9UgFBX-jyswZZ7Cik6qo7Ce/pub?w=462&h=75)

### 2-4. スケッチをダウンロードする

Arduino IDE で [ファイル] > [新規ファイル] で新しいスケッチを開き、全て削除して何も書かれていない状態にします。

以下の URL を開き、表示されたスケッチをコピーして Arduino IDE にペーストします。
[https://raw.githubusercontent.com/algyan/SORACOM/master/sketch/soracom-unified-omron_GroveDriverPack.ino](https://raw.githubusercontent.com/algyan/SORACOM/master/sketch/soracom-unified-omron_GroveDriverPack.ino)

### 2-5. Wio LTE と PC を接続して DFUモード にする

### 2-6. 新しく開いたウィンドウの ![マイコンボードに書き込むアイコン](https://docs.google.com/drawings/d/e/2PACX-1vQiO83cFcX3LCXeioiTiaao57T4SGiIV6XZzcBP6poTwssCxmo7hLpoMh5qG3btyqgzs8Q-lAoE6Q0f/pub?w=100&h=100)(マイコンボードに書き込む) をクリック

スケッチ名を保存するように言われるので、任意の名前をつけてください。

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

* [2-1.絶対圧センサーのデータを Azure IoT Central で可視化 (IoTC の設定)](../2/1-soracom-beam+azure-iot-central-IoTC.md) に進んで下さい
* [目次ページへ戻る](../index.md)

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
