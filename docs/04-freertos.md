# 04 · FreeRTOS on ESP32：双核、优先级与 SMP

## 概述

ESP-IDF 内置 **FreeRTOS**（乐鑫维护的 SMP 变体）。双核芯片上任务可指定核心亲和；Wi-Fi/BT 协议栈占用较高优先级与部分 CPU。理解优先级、栈大小与 IPC 是稳定性前提。

## 关键点

- **调度**：抢占式；同优先级时间片可配置。
- **双核**：`xTaskCreatePinnedToCore`；规划亲和，避免与协议栈恶性抢占。
- **ISR**：用 `FromISR` API；长活丢到任务。
- **Watchdog**：Task WDT / Interrupt WDT。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| API Guides 索引（搜 FreeRTOS） | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/index.html |
| FreeRTOS IoT reference（示例） | https://github.com/FreeRTOS/iot-reference-esp32 |

## 最佳实践或坑

- 应用任务勿用过高优先级抢死协议栈。
- 开栈 canary；Arduino 默认栈偏小是常见崩溃源。
- 跨核共享外设必须加锁；回调里勿长时间阻塞。

## 参考链接

- 检索：`ESP-IDF FreeRTOS SMP`、`CONFIG_FREERTOS_HZ`、`Task Watchdog Timer`
