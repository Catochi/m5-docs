# GPS - 北斗导航

<img src="assets/img/product_pics/unit/unit_gps_01.png" width="30%" height="30%">
<img src="assets/img/product_pics/unit/unit_gps_02.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.13.51a6425e6lnUwE&id=583664452054)**

<!-- :memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.13.51a6425e6lnUwE&id=583664452054)** -->

## 描述

<mark>GPS</mark>是一款集成车载设备级别的中科微北斗导航AT6558的Unit，芯片性能强悍，能获取准确全球位置信息，支持多种卫星导航系统，比如中国的BDS, 美国的GPS, 俄罗斯的GLONASS等，同时接受六个卫星导航系统的GNSS信号，并且实现联合定位、导航和授时。接M5Core的GROVE C口，M5Core通过串口与该unit通讯。其中unit还集成了信号放大芯片MAX2659。

## 特性

-  支持多种卫星导航系统，比如中国的BDS, 美国的GPS, 俄罗斯的GLONASS等
- AT6558
    - 15mA超低功耗
    - 集成射频、基带、flash
    - 工作温度：-40~85℃
<!-- -  GROVE接口，支持[UiFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc)编程 -->
-  Unit内置两个Lego插件孔，方便与Lego件结合

## 应用

- 车载定位
- 智能执法定位

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

- **[数据手册]** - [AT6558](http://www.icofchina.com/d/file/xiazai/2016-12-05/b1be6f481cdf9d773b963ab30a2d11d8.pdf) - [MAX2659](https://datasheets.maximintegrated.com/en/ds/MAX2659.pdf)

- **[CASIC多模卫星导航接收机协议规范](http://www.icofchina.com/d/file/xiazai/2017-05-02/ea0cdd3d81eeebcc657b5dbca80925ee.pdf)**

- **[上位机软件GnssToolKit3(Windows版本)](http://www.icofchina.com/d/file/xiazai/2018-05-23/2b29a8da746eec0ef1dcd9deae895298.zip)**

## 例程

### 1. Arduino IDE

```arduino
#include <M5Stack.h>

/* By default, GPS is connected with M5Core through UART2 */
HardwareSerial GPSRaw(2);

void setup() {
  M5.begin();
  GPSRaw.begin(9600);// GPS init
  Serial.println("hello");
  termInit();
}

void loop() {
  // put your main code here, to run repeatedly:
  if(Serial.available()) {
    int ch = Serial.read();
    GPSRaw.write(ch);
  }
  if(GPSRaw.available()) {
    int ch = GPSRaw.read();// read GPS information
    Serial.write(ch);
    termPutchar(ch);
  }
}
```

烧录例程`GPSRaw.ino`之后，屏幕和串口显示终端会打印如下类似的信息

```
$GPGSA,A,1,,,,,,,,,,,,,25.5,25.5,25.5*02
$BDGSA,A,1,,,,,,,,,,,,,25.5,25.5,25.5*13
$GPGSV,1,1,00*79
$BDGSV,1,1,00*68
$GNRMC,,V,,,,,,,,,,M*4E
$GNVTG,,,,,,,,,M*2D
$GNZDA,,,,,,*56
$GPTXT,01,01,01,ANTENNA OPEN*25
```

具体例程`GPSRaw.ino`请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/GPS/Arduino)。

<!-- ## 原理图

<img src="assets/img/product_pics/unit/env_sch.jpg"> -->

### 管脚映射

<table>
 <tr><td>M5Core(GROVE接口C)</td><td>ESP32串口2接收引脚U2RXD(GPIO16)</td><td>ESP32串口2发送引脚U2TXD(GPIO17)</td><td>5V</td><td>GND</td></tr>
 <tr><td>北斗导航Unit</td><td>信号发送引脚TXD</td><td>信号接收引脚RXD</td><td>5V</td><td>GND</td></tr>
</table>
