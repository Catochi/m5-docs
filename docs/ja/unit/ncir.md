# NCIR ユニット {docsify-ignore-all}

<img src="assets/img/product_pics/unit/M5GO_Unit_ncir.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_ncir_grove_a.png" width="30%" height="30%">

***

:memo:**[概要](#概要)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[サンプルコード](#サンプルコード)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[購入リンク](https://www.aliexpress.com/store/product/M5Stack-Official-NCIR-Unit-MLX90614-Contactless-Temperature-Sensor-Module-70C-382-2C-GROVE-I2C-Development-Board/3226069_32947772098.html?spm=a2g1x.12024536.productList_5885013.pic_4)**

## 概要

**<mark>NCIR</mark>**ユニットは内蔵されている**MLX90614**(非接触型の赤外線温度計)により赤外線を測定する事で、体温を測定したり、人間の動きを検出する事が可能です。**[Thermal ユニット](ja/unit/thermal)**が面で測定するのに対して、NCIRの場合は一つの点をピンポイントに測定します。I2C通信により値の取得が可能で、I2Cアドレスは**0x5A**です。

## 特徴

- 高精度
- 検出範囲: -70℃~382.2℃
- GROVE接口，支持[UIFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc)编程
- LEGO 互換ホール

## アプリケーション

- 体温測定
- 動き検出

## サンプルコード

### 1. Arduino IDE

*完全なコードは[こちら](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/NCIR)。*

```arduino
#include <M5Stack.h>
#include <Wire.h>

#define NCIR_ADDR 0x5A

// declaration
uint16_t result;
float temperature;

// initialization
Wire.begin();
M5.begin();

// read data
Wire.beginTransmission(NCIR_ADDR);Wire.write(0x07);Wire.endTransmission(false);
Wire.requestFrom(NCIR_ADDR, 2);
result = Wire.read();// Receive DATA
result |= Wire.read() << 8;// Receive DATA

// store temperature value
temperature = result * 0.02 - 273.15;
```

<img src="assets/img/product_pics/unit/unit_example/NCIR/example_unit_ncir_04.png">

### 2. UIFlow

*完全なソースコードは[こちら](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/NCIR/UIFlow)。*

<img src="assets/img/product_pics/unit/unit_example/NCIR/example_unit_ncir_03.png">

## 回路図

<img src="assets/img/product_pics/unit/ncir_sch.JPG">

### ピンマップ

<table>
 <tr><td>M5Core(GROVEインターフェースA)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>NCIR Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>

## 関連リンク

- **[公式ビデオ](https://www.youtube.com/channel/UCozgFVglWYQXbvTmGyS739w)**

- **[フォーラム](http://forum.m5stack.com/)**

- **データシート**

  - [MLX90614](https://pdf1.alldatasheet.com/datasheet-pdf/view/218977/ETC2/MLX90614.html)