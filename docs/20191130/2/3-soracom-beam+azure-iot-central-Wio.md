# 2-3.絶対圧センサーのデータを Azure IoT Central で可視化 (Wio LTE の設定)

## 1. PubSubClient ライブラリのインストール

MQTT 通信を行うにあたり PubSubClient というライブラリを利用します  
※ 公式の PubSubClient では、パケットサイズが小さいため若干不都合が発生することが確認されています。そのため、ハンズオン側で準備した fork ライブラリを使用してください

## 2. 追加のライブラリをダウンロードする

[SeeedJP/pubsubclient](https://github.com/SeeedJP/pubsubclient/releases) のページから **2.6 の ZIP** をダウンロードします

## 3. Arduino IDE を起動する

## 4. Arduino IDE の [スケッチ] > [ライブラリをインクルード] > [.ZIP 形式のライブラリをインストール...]

![wio-lte-handson / zip-lib](https://docs.google.com/drawings/d/e/2PACX-1vSyvtSl8JWQO_D5-pkwQsp0YVrrWOU76GlZohHURcIIEU-5W3PreVa9tCTUyYI94mId_y5zICWpC6xJ/pub?w=555&h=273)

先ほどダウンロードした `pubsubclient-2.6.zip` を探して「開く」をクリックすればインストール完了です

## 5. スケッチを作成する

## 5-1. Arduino IDE を起動する

## 5-2. メニューの [ツール] で [ボード: "Seeed Wio LTE Cat.1"] と表示されていることを確認する

なっていなければ一覧から "Seeed Wio LTE Cat.1" を選んでください

## 5-3. スケッチをダウンロードする

Arduino IDE で [ファイル] > [新規ファイル] で新しいスケッチを開き、全て削除して何も書かれていない状態にします。

以下の URL を開き、表示されたスケッチをコピーして Arduino IDE にペーストします。

[https://raw.githubusercontent.com/algyan/SORACOM/master/sketch/mqtt-client-beam-azure_omron.ino](https://raw.githubusercontent.com/algyan/SORACOM/master/sketch/mqtt-client-beam-azure_omron.ino)

## 6. Wio LTE を PC を接続して DFUモード にする

## 7. 新しく開いたウィンドウの ![マイコンボードに書き込むアイコン](https://docs.google.com/drawings/d/e/2PACX-1vQiO83cFcX3LCXeioiTiaao57T4SGiIV6XZzcBP6poTwssCxmo7hLpoMh5qG3btyqgzs8Q-lAoE6Q0f/pub?w=100&h=100)(マイコンボードに書き込む) をクリック

スケッチ名を保存するように言われるので、任意の名前をつけてください。

## 8. 書き込みが完了したら、Wio LTE を 通常モードにする (RSTボタンを押せば通常モードになります)

通常モードで起動次第 SORACOM Beam へデータを送信し始めます (電源投入から送信開始までは15~20秒程度かかります)

## 9. データの確認

IoTC でデバイスから送信されたデータを確認します。

![](https://docs.google.com/drawings/d/e/2PACX-1vTil8K5HXwwaExDq44VsWbcagxN4FfHBcms3qALcRYZht1_gODmcIWpJAKlvEVHZCXpRnysATXW8vAT/pub?w=926&h=504)

以上で本章は終了です。

* [3-1.気圧上昇でEメール通知](../3/1-azure-iot-central-sendmail.md)へ進んでください。
* [目次ページへ戻る](../index.md)
