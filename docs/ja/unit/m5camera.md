# M5Camera ユニット

<img src="assets/img/product_pics/unit/m5camera_01.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/m5camera_02.png" width="30%" height="30%"><br><img src="assets/img/product_pics/unit/m5camera_03.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/m5camera_04.png" width="30%" height="30%">

***

:memo:**[概要](#概要)**&nbsp;&nbsp;&nbsp;:bulb:**[クイックスタート](ja/quick_start/m5core/m5stack_core_quick_start)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[コード](#コード)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat::electric_plug:**[回路図](https://github.com/m5stack/M5-回路図/blob/master/Units/esp32-cam/M5CAM-ESP32-A1-POWER.pdf)** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[購入リンク](https://www.aliexpress.com/store/product/M5Stack-Official-ESP32-Camera-Module-Development-Board-OV2640-Camera-Type-C-Grove-Port-3D-Wifi-Antenna/3226069_32881414545.html)**

## 概要

**<mark>M5Camera</mark>**は**ESP32**、**OV2640**、4MBの**pSRAM**、**LiPoチャージャー(IP5306)**などが内蔵されています。リチウムバッテリ、MPU6050（ジャイロ＋加速度センサー）、BME280（温湿度＋気圧センサー）、マイクなどと組み合わせることでバッテリ駆動の監視システムを構築することも可能です。

## 特徴

- ESP32 スペック
  - デュアルコア Tensilica LX6 マイクロプロセッサ
  - 最大クロック 240MHz
  - 520KB SRAM
  - **4MB pSRAM**
  - **4MB Flash メモリ**
  - 802.11 b/g/n Wi-Fi
  - デュアルモード Bluetooth (classic and BLE)
  - ハードウェアアクセラレーションによる暗号化 (AES, SHA2, ECC, RSA-4096)
- CP2104 USB TTL
- OV2640 センサー
  - 出力フォーマット(8-bit):
    - YUV(422/420)/YCbCr422
    - RGB565/555
    - 8-bit 圧縮データ
    - 8/10-bit RAW RGB データ
  - 最大画像転送レート
    - UXGA/SXGA: 15fps
    - SVGA: 30fps
    - CIF: 60fps
  - スキャンモード: プログレッシブ
- カメラ スペック
  - CCD サイズ : 1/4inch
  - 視野 : 78 度
  - 最大ピクセル: 200W
- 最大解像度: 1600 * 1200
- サイズ: 25mm x 24mm
- 重量: 5g

## パッケージ内容

- 1x M5Camera
- 1x USB Type-C ケーブル

## 関連リンク

- **[公式ビデオ](https://www.youtube.com/channel/UCozgFVglWYQXbvTmGyS739w)**

- **[フォーラム](http://forum.m5stack.com/)**

- **データシート** - [ESP32](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_cn.pdf) - [OV2640](https://www.uctronics.com/download/cam_module/OV2640DS.pdf)

## コード

### ファームウェア

- **[M5Camera ファームウェア](https://github.com/m5stack/m5stack-cam-psram/tree/normal)**

### ルーチン

- **[色認識](https://github.com/m5stack/Applications-cam)**

- **[顔認識](https://github.com/m5stack/esp-who)**