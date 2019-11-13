# 2-2. 絶対圧センサーのデータを Azure IoT Central で可視化 (SORACOM の設定)

## 1. [SORACOM Web コンソール](https://console.soracom.io/) で 左上[Menu] > [SIM グループ]

[追加] で、SIMグループを作成します。グループ名は任意です。

## 2. 先ほど作成した SIMグループ をクリックし、 SORACOM Beam の設定を開きます

## 3. SORACOM Beam の「＋」をクリックし、一覧の中から **MQTT エントリポイント** をクリック

![beam-menu](https://docs.google.com/drawings/d/e/2PACX-1vTomsQdSLg-QaoYG591c1-NJYobwgXI6YqppP8h16NnxBLi8sd-QXFJvrrKrKCz6JW4d0oVp-UXCIdT/pub?w=435&h=407)

## 4. SORACOM Beam の設定では、下記の通り入力します

* 設定名: `to-IoTC`
* 種別: *Azure IoT Hub*
* プロトコル: *MQTTS* (変更し忘れが多いので注意)
* ホスト名: **2-1 でメモ帳にコピーした値 (Host name)**
* ポート番号: **8883**
* その他: **空欄**


<img src="https://docs.google.com/drawings/d/e/2PACX-1vRSDWtOWelYGw9paqusSx3AEfC4nQPGzJ_xjZD8pb7bT3e1aaWtDYNt5iDi8rRGzVmxfq8FjjH5QXnu/pub?w=471&h=879" alt="step5 MQTT PubSub with Mosquitto / beam-setting">

## 5. 「認証情報」横の「+」を選択し、下記の通り入力し、登録してください。その後、SORACOM Beam の設定も保存します。

* 認証情報 ID: **2-1 でメモ帳にコピーした値 (Credentials set ID)**
* 概要: **2-1 でメモ帳にコピーした値 (Description)**
* Access Policy name: **空欄**
* Shared access key: **2-1 でメモ帳にコピーした値 (Shared access key)**


## 6. SIM を作成したグループに登録させます

* 左上[Menu] > [SIM 管理]
* Wio LTE に取り付けている SIM を選択 > [操作] > [所属グループ変更]
* 先ほど作成した SIMグループ に所属させます。SORACOM Beam 経由で IoTC へデータを送れるようになります。

以上で本章は終了です。

* [2-3.クラウド連携 / Azure IoT Central 編 (Wio LTE の設定)](../2/3-soracom-beam+azure-iot-central-Wio.md) に進んで下さい
* [目次ページへ戻る](../index)
