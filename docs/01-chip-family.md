# 01 · 芯片家族与 SoC 对照

## 概述

乐鑫以「ESP32」为伞品牌，按系列字母区分定位：**经典 32**、**S（应用/USB）**、**C（RISC-V 互联）**、**H（802.15.4 / BLE）**、**P（高性能 HMI，无射频）**。具体 PN 还区分封装 Flash/PSRAM。下表汇总常见系列能力，细节以 [官方 SoC 页](https://www.espressif.com/en/products/socs) 与 Portfolio 为准。

## 关键点（能力速查）

| 系列 | CPU（典型） | Wi-Fi | 蓝牙 | 802.15.4 | 备注 |
| --- | --- | --- | --- | --- | --- |
| ESP32（经典） | Xtensa 单/双核 ≤240 MHz | 4 (b/g/n) | BT Classic + BLE 4.2 | 无 | 存量大；部分带 Ethernet MAC |
| ESP32-S2 | Xtensa 单核 240 MHz | 4 | 无 | 无 | USB OTG、ADC/DAC 友好 |
| ESP32-S3 | Xtensa LX7 双核 240 MHz | 4 | BLE 5 | 无 | 向量扩展、摄像头/AI 常用 |
| ESP32-S31 | RISC-V 双核（新品线） | 见官方 | 见官方 | 见官方 | 以产品页/Portfolio 为准 |
| ESP32-C2 / ESP8684 | RISC-V ~120 MHz | 4 | BLE 5 | 无 | 成本向 |
| ESP32-C3 / ESP8685 | RISC-V 160 MHz | 4 | BLE 5 | 无 | 入门 Wi-Fi+BLE 主力 |
| ESP32-C5 | RISC-V 240 MHz | **双频 Wi-Fi 6** | BLE | 有 | 2.4/5 GHz |
| ESP32-C6 | RISC-V 160 MHz | Wi-Fi 6 | BLE | Thread/Zigbee | Matter 常用端侧 |
| ESP32-C61 | RISC-V 160 MHz | Wi-Fi 6 | BLE | 无 | C6 简化向变体 |
| ESP32-H2 | RISC-V 96 MHz | **无** | BLE | Thread/Zigbee | 常与 Wi-Fi SoC 组 Border Router |
| ESP32-H4 / H21 | RISC-V | 无 | BLE | 有 | 以产品页为准 |
| ESP32-P4 | RISC-V 双核 400 MHz | **无射频** | 无 | 无 | HMI/ISP/高速外设；无线靠外挂 |

> 数值（SRAM、频点、BLE 小版本）随 PN 与硅步进变化；量产选型请打开 datasheet，勿只背本表。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| SoC 列表 | https://www.espressif.com/en/products/socs |
| Portfolio / Selector | https://products.espressif.com/ |
| 零件号解释 | https://developer.espressif.com/blog/2025/03/espressif-part-numbers-explained/ |
| Arduino 家族说明 | https://docs.espressif.com/projects/arduino-esp32/en/latest/boards/boards.html |

## 最佳实践或坑

- **P4 无 Wi-Fi**：做联网 HMI 需要第二颗无线 SoC 或模组。
- **H2 无 Wi-Fi**：适合 Thread/Zigbee 终端或与 S3/C6 组成 Border Router 参考设计。
- **C3 与 ESP8685、C2 与 ESP8684**：同系列不同市场名。
- **经典 ESP32 longevity**：新设计前核对产品生命周期承诺。

## 参考链接

- [ESP-IDF Get Started](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/index.html)
- 检索关键词：`ESP32-C5 datasheet`、`ESP32-P4 function EV board`、`ESP32-S31`
