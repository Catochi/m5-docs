# DAC - 数模转换Unit

<img src="assets/img/product_pics/units/M5GO_Unit_dac.png" width="30%" height="30%"> <img src="assets/img/product_pics/units/unit_dac_grove_a.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.28.312f425eRDFbqp&id=580257615943)**

## 描述

<mark>DAC</mark>是一款集成数字信号转模拟信号芯片的Unit，能够实现输出模拟信号，如电压、声音等，内置的DAC芯片型号是MCP4725，并且不带EEPROM。

## 特性

-  高达12位的转换精度
-  0~3.3V幅度的电压输出
-  GROVE接口，支持[UiFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc)编程
-  Unit内置两个Lego插件孔，方便与Lego件结合

## 应用

-  MP3播放器
-  mini信号发生器

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

-  **数据手册** - [MCP4725](http://pdf1.alldatasheet.com/datasheet-pdf/view/233449/MICROCHIP/MCP4725.html)

## 例程

<!-- ### 1. Arduino IDE

```c++
DHT12 dht12; //new a object
Adafruit_BMP280 bme;

float tmp = dht12.readTemperature();//temperature
float hum = dht12.readHumidity();//humidity
float pressure = bme.readPressure();//pressure
```

具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Units/DAC/Arduino)。

### 2. UIFlow

<img src="assets/img/product_pics/units/unit_example/example_unit_dac_01.png" width="30%" height="30%"> <img src="assets/img/product_pics/units/unit_example/example_unit_dac_02.png" width="55%" height="55%">

具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Units/DAC/UIFlow)。 -->

## 原理图

<img src="assets/img/product_pics/units/dac_sch.JPG">

### 管脚映射

<table>
 <tr><td>M5Core(GROVE A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>DAC Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>