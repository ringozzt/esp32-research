# 10 · ESP-NOW / Mesh / ESP-WIFI-MESH

## 概述

**ESP-NOW**：乐鑫连接层协议，无需传统 Wi-Fi 连接即可短包设备间通信，适合遥控、传感器汇聚、低延迟控制。**ESP-WIFI-MESH**：自组网多跳 Wi-Fi mesh（与「BLE Mesh」「Thread」不同）。另有社区/产品固件上的 ESP-NOW 网格封装（如 Tasmota TasMesh），属第三方能力。

## 关键点

- ESP-NOW：配对 MAC、加密可选、载荷长度有历史上限（新版本/配置下可更大——以你使用的 IDF/Arduino 版本文档为准，例如 ESPHome 曾文档化更大 payload 需新 IDF）。
- 可与 STA 共存（场景受限，需查当前 IDF）。
- ESP-WIFI-MESH：根节点联网、子节点多跳；调试复杂度高于星型。
- BLE Mesh：另一套栈，勿与 ESP-NOW 混名。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| ESP-NOW 文档 | 在 IDF 搜 `ESP-NOW`：https://docs.espressif.com/projects/esp-idf/en/stable/ |
| ESP-WIFI-MESH 指南 | API Guides → ESP-WIFI-MESH |
| ESPHome espnow 组件 | https://esphome.io/ （组件文档站内搜 espnow） |
| Tasmota（含 mesh 相关能力说明） | https://github.com/arendst/Tasmota |

## 最佳实践或坑

- 生产环境打开 ESP-NOW 加密并管理密钥。
- 信道：与路由器同频规划，避免「能连路由就不能 NOW」的配置冲突。
- Mesh 规模、延迟、吞吐量需按拓扑实测，勿用演示视频当指标。

## 参考链接

- 检索：`esp_now_init`、`ESP-WIFI-MESH root node`、`TasMesh`
