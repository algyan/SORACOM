# 2-2.絶対圧センサーのデータを Azure IoT Central で可視化 (SORACOM の設定)

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


![](https://docs.google.com/drawings/d/e/2PACX-1vSfZubqspfGJgRFN-PuViUAOlISUXTV9WyXOjqe8KU20hie6rwz1Y-2W6ou10Wfa554M2wRx5GJz7sk/pub?w=204&h=346)

## 5. 「認証情報」横の「+」を選択し、下記の通り入力し、登録してください。その後、SORACOM Beam の設定も保存します。

* 認証情報 ID: **2-1 でメモ帳にコピーした値 (Credentials set ID)**
* 概要: **2-1 でメモ帳にコピーした値 (Description)**
* Access Policy name: **空欄**
* Shared access key: **2-1 でメモ帳にコピーした値 (Shared access key)**

![](https://docs.google.com/drawings/d/e/2PACX-1vTGri5mVTFtmSIjfQ-jEmhRbMHPacA2JeTLxqS1MPJDCXDeSJ6PYdRpLlisrXmMGuDrSCSrYqaMl1XR/pub?w=339&h=344)
![](https://docs.google.com/drawings/d/e/2PACX-1vSxDJnQ-fr0NESAWyMiwhjXqVft5A07IufH07gVJFE4W_GXEGG8Qy4N-nQaz4MOeOqFYu2YxH1_jvCu/pub?w=237&h=344)

## 6. SIM を作成したグループに登録させます

* 左上[Menu] > [SIM 管理]
* Wio LTE に取り付けている SIM を選択 > [操作] > [所属グループ変更]
* 先ほど作成した SIMグループ に所属させます。SORACOM Beam 経由で IoTC へデータを送れるようになります。

以上で本章は終了です。

* [2-3.絶対圧センサーのデータを Azure IoT Central で可視化 (Wio LTE の設定)](3-soracom-beam+azure-iot-central-Wio.md) に進んで下さい
* [目次ページへ戻る](../index.md)
