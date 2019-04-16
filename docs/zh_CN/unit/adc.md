# ADC - 模数转换Unit {docsify-ignore-all}

<img src="assets/img/product_pics/unit/M5GO_Unit_adc.png" width="30%" height="30%"> <img src="assets/img/product_pics/unit/unit_adc_grove_a.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.37.3a93425e5PQbBs&id=580131730176)**

## 描述

<mark>ADC</mark> 是带自校准功能的16位模拟数字转换unit，相比ESP32芯片自带的ADC（12位）功能分辨率高了不少，意味着您可以测量更小幅值的电压等模拟量，也就是能测量更细微一倍的模拟量，比如采集心电电压做心电监护项目、做血压监测项目、高精度电压监控项目等等。unit集成的ADC芯片**ADS1100**通过I2C接口与M5的主控通讯(I2C地址为0x48)，可以设置成单周期转换和连续转换方式。

## 特性

- ADC有16位分辨率，可以设置每秒采样8、16、32、128次以进行A/D转换
- 内置可编程放大器，从而可以采集幅值更小的模拟信号
    - 放大倍数：1, 2, 4, 或 8
- 能测量0~12V的电压输入
<!-- -  GROVE接口，支持[UIFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc)编程 -->
- Unit内置两个Lego插件孔，方便与Lego件结合

## 应用

-  心电信号采集
-  血压测量
-  测力计

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

-  **数据手册** - [ADS1100](http://pdf1.alldatasheet.com/datasheet-pdf/view/619024/TI1/ADS1100.html)

## 例程

### 1. Arduino IDE

*以下仅为用法示意，并不完整。如果需要完整例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/ADC/Arduino/ADC_ADS1100)。*

```arduino
#include <M5Stack.h>
#include <Wire.h>
#include "ADS1100.h"

#define ADS1100_DEFAULT_ADDRESS 0x48

// declaration
byte error;
int8_t address;

//new a object
ADS1100 ads;

// initialization
M5.begin(true, false, false);
ads.getAddr_ADS1100(ADS1100_DEFAULT_ADDRESS);// 0x48, 1001 000 (ADDR = GND)
ads.setGain(GAIN_ONE);          // 1x gain(default)
ads.setMode(MODE_CONTIN);       // Continuous conversion mode (default)
ads.setRate(RATE_8);            // 8SPS (default)
ads.setOSMode(OSMODE_SINGLE);   // Set to start a single-conversion
ads.begin();

// read data
address = ads.ads_i2cAddress;
Wire.beginTransmission(address);
Wire.endTransmission();
ads.Measure_Differential();
```

### 2. UIFlow

具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/ADC/UIFlow)。

<img src="assets/img/product_pics/unit/unit_example/ADC/example_unit_adc_01.png">

## 原理图

<img src="assets/img/product_pics/unit/adc_sch.JPG">

### 管脚映射

<table>
 <tr><td>M5Core(GROVE接口A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>模数转换Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>