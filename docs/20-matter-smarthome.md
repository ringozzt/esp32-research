# 20 · Matter / HomeKit / 智能家居栈

## 概述

**Matter**（CSA）旨在跨生态本地互操作；在 ESP 上官方主推 **[esp-matter](https://github.com/espressif/esp-matter)**。传输可以是 **Matter-over-Wi-Fi** 或 **Matter-over-Thread**（Thread 需 802.15.4 芯片，如 C6/H2）。**HomeKit**：历史上有 HomeKit ADK / 社区方案；现今新品更常见路径是 **经 Matter 接入 Apple Home**（具体认证与芯片组合查 CSA / 苹果开发者要求）。应用层固件：**ESPHome**、**Tasmota**（自带 Matter 文档）、**Home Assistant** 生态。

## 关键点

- 数据模型：Endpoint / Cluster / Attribute。
- 佣金（commissioning）：蓝牙临时佣金 vs 已有 IP。
- Border Router：Thread 设备常需 Otbr（例如 S3+H2 类参考设计，以乐鑫当期方案为准）。
- 与厂商私有云并行时的本地控制优先级。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| esp-matter | https://github.com/espressif/esp-matter |
| CSA Matter | https://csa-iot.org/all-solutions/matter/ |
| Tasmota Matter | https://tasmota.github.io/docs/Matter/ |
| ESPHome | https://esphome.io/ |
| Home Assistant Matter | https://www.home-assistant.io/integrations/matter/ |

## 最佳实践或坑

- 选芯片前确认 **Wi-Fi-only 还是 Thread** 产品形态。
- 认证（Matter certification）耗时耗成本，开源「能连上」≠ 能上架。
- ESPHome 的 Matter 支持成熟度随版本变化——以当下文档/PR 为准，实验组件要标注风险。

## 参考链接

- 检索：`esp-matter light example`、`Thread border router ESP32-S3 ESP32-H2`
