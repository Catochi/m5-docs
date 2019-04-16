# Unit NCIR {docsify-ignore-all}

<img src="assets/img/product_pics/unit/M5GO_Unit_ncir.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_ncir_grove_a.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.43.3a93425e5PQbBs&id=580005645359)**

## 描述

**<mark>NCIR</mark>** 是一款内置了红外传感器 **MLX90614**的 Unit。使用它可以测量人体或者其他物体表面的温度。

与大多数温度传感器不同，该传感器 MLX90614 测量从远处物体反射的红外光，因此它可以感知温度而无需物理接触它们。只需将传感器指向您想要测量的位置，它就会通过吸收发射的红外波来检测温度。因为它不需要触摸它所测量的物体，所以它可以感知比大多数数字传感器更宽的温度范围：从 -70°C 到 + 380°C ！它的视场角是90度，需要在 90 度视野范围内进行测量，因此它可以方便地确定区域的平均温度。

该 Unit 与 M5Core 通过 Grove A 接口通信，IIC 地址是 0x5A。

## 特性

- 工作电压：4.5 to 5.5V
- 测量温度范围: -70℃ ~ 382.2℃
- 室温下测量精度：±0.5°C
- 视场角：90°
- GROVE 接口，支持 [UIFlow](http://flow.m5stack.com) 编程，[Arduino](http://www.arduino.cc) 编程
- Unit 内置两个 Lego 插件孔，方便与 Lego 件结合

## 包含

- 1x NCIR Unit
- 1x Grove 线

## 应用

-  人体体温测量
-  物体 ( 生物 ) 移动检测

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

-  **数据手册** - [MLX90614](https://pdf1.alldatasheet.com/datasheet-pdf/view/218977/ETC2/MLX90614.html)

## 例程

### 1. Arduino IDE

*以下仅为用法示意，并不完整。如果需要完整例程请点击[这里](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/NCIR)。*

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

*具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/NCIR/UIFlow)。*

<img src="assets/img/product_pics/unit/unit_example/NCIR/example_unit_ncir_03.png">

## 原理图

<img src="assets/img/product_pics/unit/ncir_sch.JPG">

### 管脚映射

<table>
 <tr><td>M5Core ( GROVE 接口 A )</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>红外测温 Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>