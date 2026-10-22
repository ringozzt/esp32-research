# 00 · ESP32 调研语料总览与分类法

## 概述

ESP32 是乐鑫（[Espressif Systems](https://www.espressif.com/)）推出的无线 SoC 家族品牌：从经典双核 Xtensa Wi-Fi/BT，到 RISC-V 的 C/H 系列、无射频的多媒体 P4，再到 Wi-Fi 6 / 802.15.4 的 C6、C5 等。本仓库把「芯片选型 → SDK → 连通性 → 外设与功耗 → 安全与 OTA → 应用栈（显示/AI/智能家居）→ 开源生态与工程实践」拆成可增量维护的中文专题。

**整理原则：** 不编造论文标题、GitHub stars 或未核验 URL；优先一手来源（`docs.espressif.com`、乐鑫产品页、官方 GitHub org）；不确定处给出检索关键词。

## 关键点

| 维度 | 怎么切 | 典型入口 |
| --- | --- | --- |
| 硅片 | 系列字母（经典 / S / C / H / P）与无线能力 | [01](01-chip-family.md) |
| 软件栈 | ESP-IDF 官方；Arduino / MicroPython / CircuitPython 上层 | [02](02-esp-idf.md)、[03](03-arduino-micropython.md) |
| 实时 | FreeRTOS SMP、双核亲和、优先级 | [04](04-freertos.md) |
| 无线 | Wi-Fi / BLE / Thread / Zigbee / Matter / ESP-NOW | [05](05-wireless.md)、[10](10-esp-now-mesh.md)、[20](20-matter-smarthome.md) |
| 外设与功耗 | GPIO 族、深睡、电池 | [06](06-peripherals.md)、[07](07-power-management.md) |
| 安全与更新 | Secure Boot、Flash 加密、OTA | [08](08-security.md)、[09](09-ota.md) |
| 多媒体与 AI | Camera、LVGL、ESP-DL / WHO / TFLite | [11](11-camera-lvgl.md)、[12](12-edge-ai.md) |
| 工程化 | 硬件、调试、CI、坑清单 | [17](17-hardware-design.md)–[19](19-ci-testing.md)、[23](23-pitfalls-checklist.md) |

## 代表项目 / 资源（可核验）

| 资源 | 说明 | 链接 |
| --- | --- | --- |
| ESP SoCs 产品页 | 当前在售 SoC / 模块入口 | https://www.espressif.com/en/products/socs |
| 产品选型 | 官方 Portfolio / Selector | https://products.espressif.com/ |
| ESP-IDF 稳定版文档 | 按 target 切换芯片 | https://docs.espressif.com/projects/esp-idf/en/stable/ |
| 乐鑫 GitHub | 官方组件与示例 org | https://github.com/espressif |
| 零件号解读 | Developer Portal 2025-03 | https://developer.espressif.com/blog/2025/03/espressif-part-numbers-explained/ |

## 最佳实践或坑

- **先定无线与外设，再定系列**：要 Thread/Zigbee 看 C6/H2；要 USB OTG/无 BT 看 S2；要摄像头/AI 看 S3/P4；只要便宜 Wi-Fi+BLE 看 C3/C2。
- **经典 ESP32 仍大量存量**，但新项目应核对 longevity / 是否仍需 Classic BT 或片上 Ethernet MAC。
- **文档必须选对 target**：同一功能在 `esp32` / `esp32s3` / `esp32c6` 路径下页面不同。

## 参考链接

- [Espressif Products](https://www.espressif.com/en/products)
- [ESP-IDF Programming Guide (stable)](https://docs.espressif.com/projects/esp-idf/en/stable/)
- [Arduino-ESP32 Boards 说明](https://docs.espressif.com/projects/arduino-esp32/en/latest/boards/boards.html)
