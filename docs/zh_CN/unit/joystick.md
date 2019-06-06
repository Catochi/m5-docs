# Unit JOYSTICK {docsify-ignore-all}

<img src="assets/img/product_pics/unit/M5GO_Unit_joystick_01.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_joystick_grove_a.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.66.159c425eoqBTTY&id=577874535012)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:clapper:**[相关视频](#相关视频)**

## 描述

**JOYSTICK**, 是一款摇杆控制 Unit.内部集成 MEGA328 芯片，工作原理与一般的摇杆游戏手柄类似，X、Y轴分别对应着两个 10K 的电位器.当摇杆进行动作时，产生相应的模拟信号并向M5Core输入摇杆的偏移值. Z轴方向则为一个按钮应用.

内部电路中，摇杆 X 方向连接至 MEGA328 的 A0 管脚，Y 方向连接至 A1 管脚，Z 方向连接至 A2管脚.

<img src="assets/img/product_pics/unit/M5GO_Unit_joystick_02.png" width="50%" height="50%">

该 Unit 通过GROVE A接口与M5Core进行通信，I2C地址为0x52.

## 产品特性

- X、Y 方向输出值: 10 ~ 250
- Z 方向输出值 (0: 释放; 1: 按下)
- 开发平台: Arduino, UIFlow(Blockly, Python)
- 2x LEGO 兼容孔

## 包含

- 1x JOYSTICK Unit
- 1x Grove 线

## 应用

- 游戏控制器
- 机器人远程控制

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

## 例程

### Mini Burner

>1.Mini Burner是一个简洁快速的程序烧录器，每一个产品页面里的Mini Burner都提供了一个与产品相关的案例程序.
[点击此处下载](https://m5stack.oss-cn-shenzhen.aliyuncs.com/MiniBurner/Unit/MiniBurner_Joystick.exes)

>2.下载软件后，双击运行应用程序，将M5设备通过数据线连接至电脑,选择端口参数，点击 **"Burn"** 即可开始烧录

!>3.Mini Burner烧录前需要安装有CP210X（USB驱动程序），[点击此处查看驱动安装教程](zh_CN/related_documents/M5Burner#安装串口驱动)

### 1. Arduino IDE

*以下代码仅为片段，如需获取完整代码， [请点击此处](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/JOYSTICK/Arduino).*

```arduino
#include <M5Stack.h>
#include "Wire.h"

#define JOY_ADDR 0x52

// declaration
uint8_t x_data, y_data, button_data;
char data[100];

// initialization
M5.begin();
M5.Lcd.clear();
dacWrite(25, 0);//disable the speak noise
Wire.begin(21, 22, 400000);


// read data
Wire.requestFrom(JOY_ADDR, 3);
if (Wire.available()) {
  x_data = Wire.read();// X(range: 10~250)
  y_data = Wire.read();// Y(range: 10~250)
  button_data = Wire.read();// Z(0: released 1: pressed)
  sprintf(data, "x:%d y:%d button:%d\n", x_data, y_data, button_data);
}
```

<img src="assets/img/product_pics/unit/unit_example/JOYSTICK/example_unit_joystick_04.png">

### 2. UIFlow

*以下代码仅为片段，如需获取完整代码， [请点击此处](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/JOYSTICK/UIFlow).*

<img src="assets/img/product_pics/unit/unit_example/JOYSTICK/example_unit_joystick_03.png">

## 原理图

<img src="assets/img/product_pics/unit/joystick_sch.png">

### 管脚映射

<table>
 <tr><td>M5Core(GROVE A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>JOYSTICK Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>

## 相关视频

**Joystick 的演示 - 遥控轮椅**

<video width="500" height="315" controls>
    <source src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/video/Blog/Twitch201812/M5Stack%20Joystick.mp4" type="video/mp4">
</video>

**Joystick 的演示 - 菜单界面的翻页与选择**

<video width="500" height="315" controls>
    <source src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/video/Blog/Twitch201901/Control%20M5%20With%20Joystick.mp4" type="video/mp4">
</video>
