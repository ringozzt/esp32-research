# 15 · 值得关注的开源项目与工具链

## 概述

ESP32 生态横跨「官方 SDK / 组件」「智能家居固件」「IDE 与构建」「RTOS 移植」。下列均为**可核验的公开仓库或站点**；stars 数易变，本篇不写具体数字——请打开 GitHub 页面查看。

## 关键点（分类）

| 类别 | 项目 | 链接 |
| --- | --- | --- |
| 官方 SDK | ESP-IDF | https://github.com/espressif/esp-idf |
| 官方 Arduino | arduino-esp32 | https://github.com/espressif/arduino-esp32 |
| YAML 固件 | ESPHome | https://github.com/esphome/esphome · https://esphome.io/ |
| 全能固件 | Tasmota | https://github.com/arendst/Tasmota · https://tasmota.github.io/docs/ |
| 自动化 | Home Assistant | https://www.home-assistant.io/ · ESP 集成见其文档 |
| IDE/构建 | PlatformIO Espressif32 | https://docs.platformio.org/en/latest/platforms/espressif32.html |
| 脚本 | MicroPython | https://github.com/micropython/micropython |
| 视觉/AI | esp-who / esp-dl / esp-tflite-micro | 见 [12](12-edge-ai.md) |
| Matter | esp-matter | https://github.com/espressif/esp-matter |
| 板级支持 | esp-bsp | https://github.com/espressif/esp-bsp |
| 组件注册 | ESP Component Registry | https://components.espressif.com/ |

## 代表项目 / 资源（补充）

| 资源 | 说明 | 链接 |
| --- | --- | --- |
| NuttX | 可查 Espressif / NuttX 官方对 ESP32 的移植状态 | https://nuttx.apache.org/ · 检索 `NuttX ESP32` |
| Zephyr | Zephyr RTOS Espressif 支持 | https://docs.zephyrproject.org/ · 检索 `ESP32 Zephyr` |
| OpenMQTThead 等 | 社区项目多，纳入前先核 license 与维护活跃度 | — |

## 最佳实践或坑

- 智能家居固件：分清 **ESPHome（声明式自建）** 与 **Tasmota（现成固件+Web 配置）** 工作流。
- PlatformIO 与「原生 IDF 工具链」可能并存（ESPHome 等已迁移默认工具链——以各自 release note 为准）。
- 复制粘贴多年前博客的 `board:` 名，常与新版 platform 包不兼容。

## 参考链接

- [Espressif GitHub org](https://github.com/espressif)
- [Tasmota Matter 文档](https://tasmota.github.io/docs/Matter/)
