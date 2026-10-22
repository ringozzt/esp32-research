# 07 · 电源管理、深睡与电池

## 概述

ESP32 系列提供多种低功耗模式（如 Modem-sleep、Light-sleep、Deep-sleep）与 **ULP / LP 核**（视芯片）在主 CPU 关闭时做有限采集。电池产品要同时设计：**硬件电源路径**、**唤醒源**、**Wi-Fi 连接策略**、**测量方法**（真电池 vs USB）。

## 关键点

- **Deep-sleep**：RAM 基本掉电（RTC 慢内存可保留）；唤醒：定时、EXT0/1、触摸、ULP 等（按芯片）。
- **Light-sleep**：外设可保持；适合短空闲。
- **自动调光频 / DFS**：`esp_pm` 配置；与外设时钟需求冲突时需锁频。
- **Wi-Fi 功耗**：长连 vs 周期上线；TCP keepalive、MQTT 心跳要算占空比。
- **测量**：串联电流计；注意 USB-UART 芯片灌电流造成的假读数。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Sleep Modes 指南 | 在 stable 文档搜 `Sleep Modes` / Deep-sleep |
| ULP 文档 | 搜 `ULP Coprocessor` |
| Power Management | 搜 `Power Management` / `esp_pm` |

示例官方路径形态（版本/target 变化时以站内搜索为准）：  
`https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/sleep_modes.html`

## 最佳实践或坑

- Deep-sleep 后外设与 Wi-Fi 状态机要按**冷启动**重建。
- 开启 Secure Boot 时，深睡快启选项可能受限（见 Bootloader 文档对 `SKIP_VALIDATE_IN_DEEP_SLEEP` 的约束）。
- 电池：选 LDO/DCDC、电池保护、充电 IC；GPIO 漏电与分压电阻是 μA 级杀手。
- 不要用「官网宣传 μA」代替你的 BOM 实测。

## 参考链接

- [Bootloader / Deep-sleep 相关](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/bootloader.html)
- 检索：`ESP32 deep sleep current measurement`、`ULP RISC-V ADC`
