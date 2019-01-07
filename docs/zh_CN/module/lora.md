# LORA - LoRa节点模块(433MHz)

<img src="assets/img/product_pics/module/module_lora_01.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_lora_02.png" width="30%" height="30%"> <img src="assets/img/product_pics/module/module_lora_03.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.5-c.w4002-1172588093.70.6c2275f4nUJEfh&id=559302217850)**

<!-- :memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.5-c.w4002-1172588093.70.6c2275f4nUJEfh&id=559302217850)** -->

## 描述

<mark>LoRa</mark>是内置了Ra-02小模组的LoRa模块。堆叠了M5Core之后，你可以用UiFlow、Arduino和MicroPython来编程它。

M5Stack LoRa模块适用于长距离通信，结合多个LoRa模块，能组成长达1-2公里的物联网低功耗通信网络。它克服了传统物联网通信中长距离可是高功耗的难点。与蓝牙WIFI等通信技术相互弥补。

## 特性

-  LoRa模块型号RA-02
-  支持FSK, GFSK, MSK, GMSK调制解调制式
-  长距离低功耗
-  内置天线

## 包含

-  1x M5Stack LoRa模块

## 应用

-  自动抄表系统
-  楼宇自动化
-  远程灌溉系统

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

- **[LoRa模块信息](http://wiki.ai-thinker.com/lora) (LoRa)**

?> 如果堆叠了LoRa模块之后，上电，可是M5Core不能正常显示或者有其他显示问题时，建议在`m5.begin();`语句之前加入如下语句。因为GPIO5连接到LoRa模块的NSS引脚，该引脚在系统上电的时候需要上拉，从而避免LCD不能显示。

```arduino
    pinMode(5,OUTPUT);
    digitalWrite(5,HIGH);
    m5.begin();
```

## 例程

### Arduino IDE

这是两个LORA模块点对点通信的例程，一个作为信号发射节点，一个作为信号接收节点。

*以下仅为用法示意，并不完整。如果需要完整例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Module/LORA/Arduino)*

```arduino
#include <M5Stack.h>
#include <M5LoRa.h>

// declaration
static uint32_t counter;

// initialization
// override the default CS, reset, and IRQ pins (optional)
LoRa.setPins(); // default set CS, reset, IRQ pin
M5.Lcd.println("LoRa Sender");
// frequency in Hz (433E6, 866E6, 915E6)
LoRa.begin(433E6);

// send data
LoRa.beginPacket();
LoRa.print("hello ");
LoRa.print(counter);// lora send data
LoRa.endPacket();
```

```arduino
/*
    LoRaReceiver.ino
*/
#include <M5Stack.h>
#include <M5LoRa.h>

// initialization
M5.begin();
// override the default CS, reset, and IRQ pins (optional)
LoRa.setPins();// default set CS, reset, IRQ pin
// frequency in Hz (433E6, 866E6, 915E6)
LoRa.begin(433E6);

// try to parse packet
int packetSize = LoRa.parsePacket();
if (packetSize) {
  // read packet
  while (LoRa.available()) {
    char ch = (char)LoRa.read();
    M5.Lcd.print(ch);
  }
  // print RSSI of packet
  M5.Lcd.print("\" with RSSI ");
  M5.Lcd.println(LoRa.packetRssi());
}
```

<img src="assets/img/product_pics/module/module_example/LORA/example_module_lora_01.png">

<!-- ## 原理图 -->
