# LidarBot

## 描述

<mark>LidarBot</mark>是一款以室内导航为基础的四轮小车。车体装载了激光雷达、四个麦克纳姆轮、车轮控制低板(主控芯片是MEGA328)、前后RGB灯带(共16颗)、M5Core主控、多个LEGO孔。车与远程遥控手柄之间通过ESP-NOW实时通信，而小车主控接收到控制信号后，通过规定的协议格式实现控制车轮和RGB灯带等。除了能控制小车灵活地前后左右移动之外，还能在小车主控和手柄主控各自的显示屏上显示室内地形。

## 特性

- 雷达: 8m @ 6Hz
- 支持Arduino编程
- 兼容LEGO件

## 控制底板的协议

*协议格式：帧头(命令类型)+数据帧+帧尾*

| 协议对象          | 协议格式                               |
| :-------------:  |:------------------------------------: |
| 控制车轮          | 0xAA,SpeedX,SpeedY,SpeedZ,SpeedA,0x55 |
| 控制单颗RGB       | 0xAB,LedIndex,R,G,B,0x55              |
| 控制前向RGB灯带    | 0xAC,R,G,B,0x55                       |
| 控制后向RGB灯带    | 0xAD,R,G,B,0x55                       |
| 控制全部RGB       | 0xAE,R,G,B,0x55                       |
| 控制舵机0        | 0xAF,Angle,0x55                       |
| 控制舵机1        | 0xB0,Angle,0x55                       |

## 参数

- 通信参数
    - 车体的M5Core主控与激光雷达传感器（RXD <-> GPIO16）
    串口参数：230400bps，8位数据位，无奇偶校验，1位停止位
    - 车体的M5Core主控与车轮控制底板（TXD <-> GPIO17）
    串口参数：115200bps，8位数据位，无奇偶校验，1位停止位
- 接口
    - 舵机0 <-> A0(MEGA328)
    - 舵机1 <-> A1(MEGA328)
    - NeoPixelRGB <-> 11(MEGA328)

## 包含

- 1x LidarBot
- 1x 远程遥控手柄
- 2x 电池(1300mAh @ 11.1V)
- 1x 电池充电器
- 1x Type-C USB线

## 应用

- 室内导航
- 自主走迷宫
- 路径规划
- 自动驾驶

## 文档
- **例程** - [Arduino](https://github.com/m5stack/Applications-LidarBot/tree/master/LidarBot/Example) - [MicroPython]()
- **[快速上手](zh_CN/file_to_display_null)**
- **[旗舰店](https://www.aliexpress.com/store/product/M5Stack-New-Lidar-Bot-Mini-Car-Lidar-8m-6Hz-McNamm-Wheels-NeoPixel-LED-Bar-with-ESP32/3226069_32951134988.html?spm=a2g1y.12024536.productList_5885013.subject_7)**

<figure>
    <img src="assets/img/product_pics/applications/lidarbot_1.jpg">
</figure>

<figure>
    <img src="assets/img/product_pics/applications/lidarbot_2.jpg">
</figure>

<figure>
    <img src="assets/img/product_pics/applications/lidarbot_3.jpg">
</figure>

<figure>
    <img src="assets/img/product_pics/applications/lidarbot_4.jpg">
</figure>