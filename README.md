# ESP32 调研语料

面向选型、固件架构与工程落地的**中文** ESP32 / ESP-IDF 研究仓库：芯片家族、无线与 Matter、外设与功耗、安全与 OTA、显示与边缘 AI、开源生态与避坑清单。  
**整理日期：** 2026-10-24（Asia/Shanghai）  
**原则：** 不编造论文标题、GitHub stars 或未核验链接；优先 [Espressif 官方文档](https://docs.espressif.com/)与可复核的开源仓库；不确定处给检索关键词。

## ESP32 是什么

乐鑫（Espressif）以 **ESP32** 为伞品牌，提供带 Wi-Fi / 蓝牙 / 802.15.4 等能力的系列 SoC 与模组，官方软件栈为 **ESP-IDF**（其上还有 Arduino-ESP32、MicroPython、ESPHome、Tasmota 等生态）。经典双核 Xtensa「ESP32」、S 系列、RISC-V 的 C/H 系列、无片上射频的 P 系列等定位不同——**先查无线与外设矩阵，再写代码**。

## 芯片家族速查

| 系列 | CPU（典型） | Wi-Fi | 蓝牙 | 802.15.4 | 一句话 |
| --- | --- | --- | --- | --- | --- |
| ESP32 经典 | Xtensa ≤240 MHz | 4 | Classic + BLE | 无 | 存量最大；部分带 Ethernet MAC |
| ESP32-S2 | Xtensa 240 MHz | 4 | 无 | 无 | USB OTG / 模拟外设 |
| ESP32-S3 | Xtensa LX7 双核 240 MHz | 4 | BLE 5 | 无 | 摄像头 / 边缘 AI 常用 |
| ESP32-C3 | RISC-V 160 MHz | 4 | BLE 5 | 无 | 入门 Wi-Fi+BLE |
| ESP32-C6 | RISC-V 160 MHz | Wi-Fi 6 | BLE | 有 | Matter / Thread 常用 |
| ESP32-C5 | RISC-V 240 MHz | 双频 Wi-Fi 6 | BLE | 有 | 2.4 + 5 GHz |
| ESP32-H2 | RISC-V 96 MHz | 无 | BLE | 有 | Thread/Zigbee 端或组 BR |
| ESP32-P4 | RISC-V 双核 400 MHz | 无 | 无 | 无 | 高阶 HMI；无线靠外挂 |
| C2 / C61 / S31 / H4… | 见产品页 | 见产品页 | 见产品页 | 见产品页 | 以 [SoC 列表](https://www.espressif.com/en/products/socs) 为准 |

> 细表与坑见 [docs/01-chip-family.md](docs/01-chip-family.md)。SRAM/频点/PN 以 datasheet 为准。

## 为何有本仓库

把分散的官方文档、开源固件与工程经验收成**可检索专题 + 每日 digests**，方便中文语境下持续跟踪（新硅片、IDF 大版本、Matter、安全加固），而不是停留在单次博客收藏。

## 文档目录（`docs/`）

| # | 文档 | 一句话 |
| --- | --- | --- |
| 00 | [总览与分类法](docs/00-overview-taxonomy.md) | 怎么读本仓库 |
| 01 | [芯片家族对照](docs/01-chip-family.md) | 经典 / S / C / H / P |
| 02 | [ESP-IDF 与构建](docs/02-esp-idf.md) | CMake、组件、分区 |
| 03 | [Arduino / MicroPython / CP](docs/03-arduino-micropython.md) | 四条软件路径 |
| 04 | [FreeRTOS 与双核](docs/04-freertos.md) | SMP、优先级、WDT |
| 05 | [无线能力地图](docs/05-wireless.md) | Wi-Fi / BLE / Thread / Zigbee |
| 06 | [外设](docs/06-peripherals.md) | GPIO…RMT…TWAI |
| 07 | [电源与深睡](docs/07-power-management.md) | 电池与 μA 级陷阱 |
| 08 | [安全](docs/08-security.md) | Secure Boot / Flash 加密 |
| 09 | [OTA](docs/09-ota.md) | HTTPS、签名、回滚 |
| 10 | [ESP-NOW / Mesh](docs/10-esp-now-mesh.md) | 短包与自组网 |
| 11 | [摄像头 / LVGL](docs/11-camera-lvgl.md) | S3 / P4 多媒体 |
| 12 | [边缘 AI](docs/12-edge-ai.md) | ESP-DL / WHO / TFLite |
| 13 | [Ethernet / 工业](docs/13-ethernet-industrial.md) | PHY、TWAI、PoE |
| 14 | [USB / TinyUSB](docs/14-usb-otg-tinyusb.md) | OTG 与 Serial-JTAG |
| 15 | [开源项目](docs/15-opensource-projects.md) | ESPHome / Tasmota / PIO… |
| 16 | [论文方向](docs/16-papers-academic.md) | 检索关键词，不编造题录 |
| 17 | [硬件设计](docs/17-hardware-design.md) | 天线、电源、PSRAM |
| 18 | [调试](docs/18-debugging.md) | Monitor / JTAG / heap |
| 19 | [CI 与测试](docs/19-ci-testing.md) | Unity / Host / 矩阵 |
| 20 | [Matter / 智能家居](docs/20-matter-smarthome.md) | esp-matter、HA |
| 21 | [LoRa / 蜂窝外挂](docs/21-lora-cellular.md) | 模组与合规 |
| 22 | [社区资源](docs/22-community-resources.md) | 官方与论坛导航 |
| 23 | [坑与清单](docs/23-pitfalls-checklist.md) | 发布前 gate |
| 24 | [路线与 digests](docs/24-roadmap-digests.md) | 增量如何回写专题 |

## 其它文件

| 路径 | 说明 |
| --- | --- |
| [GAP-ANALYSIS.md](GAP-ANALYSIS.md) | 已覆盖 / 缺口 / 下一步 |
| [digests/](digests/) | 每日增量（`YYYY-MM-DD.md`） |
| [digests/README.md](digests/README.md) | 日报约定 |
| [digests/_TEMPLATE.md](digests/_TEMPLATE.md) | 日报模板 |

## 怎么读

1. 选型：`01` → `05` → `23`  
2. 量产固件：`02` → `08` → `09` → `19`  
3. 智能家居：`15` → `20` → `10`  
4. 显示 / AI：`11` → `12`  
5. 每日更新：看 `digests/`，再对照 `24`

**最新日报：** [digests/2026-10-24.md](digests/2026-10-24.md)

## 一手入口

- SoC：https://www.espressif.com/en/products/socs  
- ESP-IDF stable：https://docs.espressif.com/projects/esp-idf/en/stable/  
- GitHub org：https://github.com/espressif  
