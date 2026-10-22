# 11 · 摄像头 / LVGL / 显示 / 多媒体

## 概述

**ESP32-S3** 是社区摄像头 + 小屏 AI 的主流；**ESP32-P4** 面向更高阶 HMI（ISP、高速接口等，无片上 Wi-Fi）。显示常用 SPI/RGB/MIPI（视芯片）面板 + **LVGL**；摄像头常用 `esp32-camera` 组件或更新的 `esp_video` 路径（P4 等）。音频走 I2S / 官方 ADF。

## 关键点

- 摄像头：DVP/MIPI-CSI（芯片而定）、PSRAM 帧缓冲、JPEG 编码。
- LVGL：UI 任务优先级、局部刷新、DMA 拷屏。
- 开发板：ESP32-S3-EYE、Korvo、P4 Function EV Board 等。
- 与 AI：检测管线见 [12](12-edge-ai.md)。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| esp32-camera | https://github.com/espressif/esp32-camera |
| ESP-WHO（视觉示例 + LVGL） | https://github.com/espressif/esp-who |
| ESP-BSP | https://github.com/espressif/esp-bsp |
| LVGL | https://github.com/lvgl/lvgl |
| ESP-ADF（音频） | https://github.com/espressif/esp-adf |
| ESP-VISION 文档（P4 等） | https://docs.espressif.com/projects/esp-vision/en/latest/ |

## 最佳实践或坑

- Octal PSRAM 与 Flash 引脚/时序：用官方模组或严格跟参考设计。
- 帧率：camera 与推理异步（WHO 新架构强调这点）比「一个循环里全做」更稳。
- 供电：摄像头+屏峰值电流足够，否则褐屏/断连。

## 参考链接

- 检索：`ESP32-S3-EYE`、`lvgl esp_lcd`、`MIPI CSI ESP32-P4`
