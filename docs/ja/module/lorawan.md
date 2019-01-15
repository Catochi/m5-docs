# LoRaWAN モジュール(433/470MHz和868/915MHz)

<img src="assets/img/product_pics/module/module_lora_01.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_lora_02.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_lora_03.png" width="30%" height="30%">

***

:memo:**[概要](#概要)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[サンプルコード](#サンプルコード)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[回路図](#回路図)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[購入リンク](https://www.aliexpress.com/store/product/M5Stack-New-LoRaWAN-Module-433-470Mhz-868-915MHz-with-Internal-Antenna-and-MCX-External-Antenna-Port/3226069_32953098569.html?spm=a2g1y.12024536.productList_5885011.pic_2)**

## 概要

**<mark>LoRaWAN</mark>**モジュールはLoRaチップ(SX1276)とMCU内蔵の小型LoRa端末モジュールです。完全なLoRaプロトコルスタックが組み込まれており、UARTまたはsimple ATコマンドを利用してLoRaWANモジュールを開発することができます。

デフォルトUART config: "9600, 8, n, 1" (8ビットデータ, ノーパリティ, 1ストップビット)

?> "LoRaWAN"シルクスクリーンの隣の5つの穴はLoRaWANモジュールのファームウェアアップデート用です。

## 特徴

- サポートバンド: 433/470MHz , 868/915MHz
- データレート: 0.018-38.4kbps
- 出力: 17 ± 0.5dbm
- ADR(Adaptive Data Rate)サポート
- アンテナ内蔵

## パッケージ内容

- 1x LoRaWAN　モジュール

## アプリケーション

- オートメーターリーダー
- スマートホーム
- リモート灌漑システム

## ピンマップ

|RHF76-052_UART | ESP32 Chip |
|:--------------|:-----------|
|RXD | GPIO16 |
|TXD | GPIO17 |

## 関連リンク

- **[公式ビデオ](https://www.youtube.com/channel/UCozgFVglWYQXbvTmGyS739w)**

- **[フォーラム](http://forum.m5stack.com/)**

- **データシート** - [RHF76-052 wiki](http://wiki.ai-thinker.com/sx127x-052) - [ATコマンド for LoRaWAN](http://wiki.ai-thinker.com/_media/rhf-ps01509_module_lorawan_class_ac_at_command_specification_-_v4.4.pdf)

## サンプルコード

### Arduino IDE

これはピアツーピア通信のためのルーチンです.

*特定のルーチンをクリックしてください[ルーチン](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Module/LORAWAN/Arduino)。*

```arduino
/*
    Master.ino
*/

#include <M5Stack.h>

// entry test mode
String cmd_test_mode = "AT+Mode=Test";
// Configure the modem,like Freq, SF, BW, Preamble length, TX output power
String cmd_rfconf = "AT+TEST=RFCFG,472.3,8,250,8,8,20";
// send data as HEX format
String cmd_send_data = "AT+TEST=TXLRPKT,\"30 31 32 33 34 35\"";

void setup() {
  M5.begin();
  Serial.begin(9600);
  Serial2.begin(9600, SERIAL_8N1, 16, 17);

  delay(1000);// delay for lorawan power on
  /* LoRaWAN Init */
  Serial2.println(cmd_test_mode);
  delay(500);
  Serial2.println(cmd_rfconf);
  delay(500);
}

void loop() {
  if(M5.BtnA.wasPressed()) {
    Serial2.println(cmd_send_data);
    Serial.println(cmd_send_data);
  }
  M5.update();
}
```

```arduino
/*
    Slaver.ino
*/

#include <M5Stack.h>

// entry test mode
String cmd_test_mode = "AT+Mode=Test";
// Configure the modem,like Freq, SF, BW, Preamble length
String cmd_rfconf = "AT+TEST=RFCFG,472.3,8,250,8,8,20";
// allow to receive data
String cmd_receive_data = "AT+TEST=RXLRPKT";

void setup() {
  M5.begin();
  Serial.begin(9600);
  Serial2.begin(9600, SERIAL_8N1, 16, 17);
  delay(1000);// delay for lorawan power on
  /* LoRaWAN Init */
  Serial2.println(cmd_test_mode);
  delay(500);
  Serial2.println(cmd_rfconf);
  delay(500);
  Serial2.println(cmd_receive_data);
  delay(500);
}

void loop() {
  if(Serial2.available()) {
    int ch = Serial2.read();
    M5.Lcd.print((char)ch);
    Serial.write(ch);
  }
}
```

## 回路図

<img src="assets/img/product_pics/module/lorawan_sch.png">