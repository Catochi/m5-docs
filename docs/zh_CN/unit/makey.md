# MAKEY - 创意键盘 {docsify-ignore-all}

<img src="assets/img/product_pics/unit/M5GO_Unit_makey.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_makey_grove_a.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/M5GO_Unit_makey_02.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.51.159c425eoqBTTY&id=577636777112)**

## 描述

**<mark>MAKEY</mark>** 是一款内置 MEGA328P 芯片、蜂鸣器和 RGB 灯的 Unit，并附带 16 个引脚。

该 Unit 与 M5Core 通过 GROVE A 接口 ( IIC ) 通信，其 I2C 地址是 0x51 。


**使用方法：**

1）只是 unit 上的蜂鸣器发声

一根杜邦线或普通导线接 unit 的 GND 孔，并另一端被握在左手；

另一根杜邦线一端握右手，另一端触碰 unit 上的音调孔，就会发出对应音调。

2）m5core 上的喇叭发声

unit 通过 GROVE 线连接至 m5core 的接口 A 后，烧录[例程](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/Makey_NewVersion/Arduino/Makey_new_version)。

一根杜邦线或普通导线接 unit 的 GND 孔，并另一端被握在左手；

另一根杜邦线一端握右手，另一端触碰 unit 上的音调孔，m5core 的喇叭会发出对应音调。

## 特性

-  内置 Mega328p 芯片，蜂鸣器，RGBLed
<!-- -  16 Keys Fruit Piano(PD0-7 & PB0-5), 1 NeoPixel pin(PC2) and 1 Buzzer pin(PC3) -->
-  GROVE 接口，支持 [UIFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc) 编程
-  Unit 内置两个 Lego 插件孔，方便与 Lego 件结合

## 包含

- 1x MAKEY Unit
- 1x Grove 线

## 应用

- 水果键盘

<img src="assets/img/product_pics/unit/M5GO_Unit_makey_05.png" width="40%" height="40%">

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

- **[模块内 MEGA328 固件](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/Makey_NewVersion/firmware_328p)**

## 例程

### 1. Arduino IDE

*以下仅为用法示意，并不完整。如果需要完整例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/Makey_NewVersion/Arduino/Makey_new_version)。*

```arduino
#include <M5Stack.h>
#include <Wire.h>

// initialization
M5.begin();
pinMode(21, INPUT); pinMode(22, INPUT);
Wire.begin();// Init I2C

// read data
Wire.requestFrom(MAKEY_ADDR, 2);
while (Wire.available()) {
  Key1 = Wire.read();//read data from MAKEY
  Key2 = Wire.read();//read data from MAKEY
  tone_key = (Key2<<8) | Key1;// the following picture will explain "tone_key"
}
```

<img src="assets/img/product_pics/unit/unit_example/MAKEY/tone_key_pitch_zh_CN.png">

<img src="assets/img/product_pics/unit/M5GO_Unit_makey_04.png" width="30%" height="30%">

### 2. UIFlow

*具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/MAKEY/UIFlow)。*

<img src="assets/img/product_pics/unit/unit_example/MAKEY/example_unit_makey_02.png">

## 原理图

<img src="assets/img/product_pics/unit/makey_sch.png">

### 管脚映射

<table>
 <tr><td>M5Core ( GROVE 接口 A )</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>MAKEY 创意键盘 Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>

<img src="assets/img/product_pics/unit/M5GO_Unit_makey_03.png" width="30%" height="30%">