# TRACE - 巡线 Unit {docsify-ignore-all}

<img src="assets/img/product_pics/unit/unit_trace_01.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_trace_02.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.12.4c32425eGaqxO8&id=587199991600)**

## 描述

**<mark>TRACE</mark>** 是一款内置 4 组红外发射 LED 和红外敏感光电晶体管的巡线 Unit。它可以将数字信号输出到微控制器，这样机器人可以稳定地跟随白色背景上的黑线，反之亦然。

该 Unit 与 M5Core 通过 GROVE A 接口 ( IIC ) 通信，其 I2C 地址是 0x5A 。


<img src="assets/img/product_pics/unit/unit_trace_03.png" width="60%" height="60%">

## 特性

- 工作范围：反射面距离光电对管面小于 11mm
- GROVE 接口，支持 [UIFlow](http://flow.m5stack.com) 编程，[Arduino](http://www.arduino.cc) 编程

## 包含

- 1x TRACE Unit
- 1x Grove 线

## 应用

- 机器人巡线

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

- **[模块内 MEGA328 固件](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TRACE/firmware_328p)**

## 例程

### 1. Arduino IDE

*以下仅为用法示意，并不完整。如果需要完整例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TRACE/Arduino)。*

```arduino
#include <M5Stack.h>
#include "Wire.h"

#define TRACE_ADDR 0x5a

// declaration
#define VALUE_SPLIT
uint8_t value;
int SensorArray[4] = {0};

// initialization
m5.begin();
Serial.begin(115200);
Wire.begin();


// read data
Wire.beginTransmission(TRACE_ADDR);
Wire.write(0x00);
Wire.endTransmission();
Wire.requestFrom(TRACE_ADDR,1);
while(Wire.available()){
    value = Wire.read();
}
SensorArray[3] = (value&0x08)>>3;
SensorArray[2] = (value&0x04)>>2;
SensorArray[1] = (value&0x02)>>1;
SensorArray[0] = (value&0x01)>>0;
```

<img src="assets/img/product_pics/unit/unit_trace_04.png">

### 2. UIFlow

*具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TRACE/UIFlow)。*

<img src="assets/img/product_pics/unit/unit_example/TRACE/example_unit_trace_01.png">

## 原理图

<img src="assets/img/product_pics/unit/trace_sch.png">

### 管脚映射

<table>
 <tr><td>M5Core(GROVE接口A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>TRACE Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>

## 相关视频

**TRACE 的演示**

<video width="500" height="315" controls>
    <source src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/video/Blog/Twitch201901/lidarbot.mp4" type="video/mp4">
</video>