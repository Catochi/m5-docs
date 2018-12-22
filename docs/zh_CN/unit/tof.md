# TOF - 红外测距Unit

<img src="assets/img/product_pics/unit/M5GO_Unit_tof.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/unit_tof_grove_a.png" width="30%" height="30%">

***

:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[例程](#例程)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](#原理图)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-1172588106.40.3a93425e5PQbBs&id=580005945330)**

## 描述

<mark>ToF</mark>是一款用"Time-to-Flight"传感器(VL53L0X)发出940nm的激光来测量距离的Unit，相比其他测距传感器，具有更高的精度，可以直接确定以毫米为单位的目标物体的距离。不到30ms即可提供最长2米的毫米级的绝对距离读值。

该Unit与M5Core通过PORT A(I2C)通信。I2C地址为0x29

## 特性

-  高精度
-  测量距离最大2m
-  激光波长: 940nm
-  GROVE接口，支持[UiFlow](http://flow.m5stack.com)编程，[Arduino](http://www.arduino.cc)编程
-  Unit内置两个Lego插件孔，方便与Lego件结合

## 应用

- 手势控制

- 激光测距

- 3D结构光成像(3D感测)

- 摄像机辅助（超快速自动对焦和景深图）

## 相关链接

- **[官方频道视频](https://i.youku.com/i/UNjE1ODA2MzE0OA==?spm=a2hzp.8253869.0.0)**

- **[官方论坛](http://forum.m5stack.com/)**

-  **数据手册** - [VL53L0X](https://pdf1.alldatasheet.com/datasheet-pdf/view/948120/STMICROELECTRONICS/VL53L0X.html)

## 例程

### 1. Arduino IDE

```c++
#define SYSRANGE_START  0x00
#define RESULT_RANGE_STATUS 0x14
#define ToF_ADDR 0x29   //the IIC address of ToF

write_byte_data_at(SYSRANGE_START, 0x01);   //start measure
read_block_data_at(RESULT_RANGE_STATUS, 12);    //read 12 bytes once
dist = makeuint16(gbuf[11], gbuf[10]);  //split distance data and save at "dist"
```

具体例程`MeasureDistance.ino`请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TOF/Arduino)。

<!-- ### 2. UIFlow

<img src="assets/img/product_pics/unit/unit_example/example_unit_tof_01.png" width="30%" height="30%"> <img src="assets/img/product_pics/unit/unit_example/example_unit_tof_02.png" width="55%" height="55%">

具体例程请点击[这里](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TOF/UIFlow)。 -->

## 原理图

<img src="assets/img/product_pics/unit/tof_sch.JPG">

### 管脚映射

<table>
 <tr><td>M5Core(GROVE A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>TOF Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>