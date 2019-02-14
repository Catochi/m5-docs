# SERVO モジュール {docsify-ignore-all}

<img src="assets/img/product_pics/module/module_servo_01.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_servo_02.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_servo_03.png" width="30%" height="30%">

***

:memo:**[概要](#概要)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[サンプルコード](#サンプルコード)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[回路図](#回路図)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[購入リンク](https://www.aliexpress.com/store/product/M5Stack-New-SERVO-Module-Board-12-Channels-Servo-Controller-with-MEGA328-Inside-Power-Adapter-6-24V/3226069_32951356502.html?spm=a2g1y.12024536.productList_5885011.pic_0)**

## 概要

**<mark>SERVO</mark>**モジュールは、12ウェイサーボモータを同時に駆動できるサーボモータドライバモジュールです。(現在、最大電流の制限により、駆動できるサーボモータの最大数は9です。すぐにアップグレード版を公開します。）

サーボモータをコントロールするのはとても簡単です。Arduino IDEで2〜3行のコードを書くか、UiFlowで2-3ブロックをドラッグ&ドロップするだけで、一度に多くのサーボモータを駆動できます。

サーボはGROVEインタフェース（I2C）を介してM5Coreと通信します。 I2Cアドレスは<mark>0x53</mark>です。

## 特徴

- 12サーボモータ同時駆動可能
- 電源範囲：6-12V
- Arduino IDEサポート
- UiFlowサポート

## パッケージ内容

- 1x SERVO モジュール
- 1x 6-12V 電源インターフェース

## アプリケーション

- ヒューマノイドロボット
- バイオニック多関節ロボット
- カメラ用3軸ヘッド

## 関連リンク

- **[公式ビデオ](https://www.youtube.com/channel/UCozgFVglWYQXbvTmGyS739w)**

- **[フォーラム](http://forum.m5stack.com/)**

- **[モジュール内のMEGA328ファームウェア](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Module/SERVO/firmware_328p)**

## サンプルコード

### 1. Arduino IDE

*例程下载请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Module/SERVO/Arduino)。*

```arduino
#include <Arduino.h>
#include <M5Stack.h>
#include <Wire.h>

#define SERVO_ADDR 0x53
void setup() {
    M5.begin(true, false, true);
    M5.Lcd.setTextFont(4);
    M5.Lcd.setCursor(70, 100);
    M5.Lcd.print("Servo Example");

    Wire.begin(21, 22, 100000);
}

// addr 0x01 means "control the number 1 servo by us"
void Servo_write_us(uint8_t number, uint16_t us) {
    Wire.beginTransmission(SERVO_ADDR);
    Wire.write(0x00 | number);
    Wire.write(us & 0x00ff);
    Wire.write(us >> 8 & 0x00ff);
    Wire.endTransmission();
}

// addr 0x11 means "control the number 1 servo by angle"
void Servo_write_angle(uint8_t number, uint8_t angle) {
    Wire.beginTransmission(SERVO_ADDR);
    Wire.write(0x10 | number);
    Wire.write(angle);
    Wire.endTransmission();
}

void loop() {
    for(uint8_t i = 0; i < 12; i++){
        Servo_write_us(i, 700);
        // Servo_write_angle(i, 0);
    }
    delay(1000);
    for(uint8_t i = 0; i < 12; i++){
        Servo_write_us(i, 2300);
        // Servo_write_angle(i, 180);
    }
    delay(1000);
}
```

### 2. UIFlow

*特定のルーチンをクリックしてください[ルーチン](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Module/SERVO/UIFlow).*

<img src="assets/img/product_pics/module/module_example/SERVO/example_module_servo_01.png">

## 回路図

<img src="assets/img/product_pics/module/servo_sch.png">