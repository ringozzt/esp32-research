# 18 · 调试：JTAG、OpenOCD、监视器、堆追踪

## 概述

日常：**`idf.py monitor`** 看日志 + 核心转储。深度：**JTAG + OpenOCD + GDB**（或 VS Code/Eclipse 插件）。运行时：**heap tracing、task snapshot、apptrace**。启用 Flash Encryption / Secure Boot 后 JTAG 常被关闭，需在实验室阶段保留调试策略。

## 关键点

- UART / USB-Serial-JTAG 控制台；`ESP_LOG` 级别。
- `CONFIG_ESP_SYSTEM_PANIC_*`、core dump 到 Flash/UART。
- OpenOCD：官方适配各 target；接线与适配器（如 USB-JTAG、外部探针）。
- Heap：`heap_caps_print_heap_info`、leak tracing。
- 双核：GDB 线程与核切换。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| JTAG Debugging 指南 | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/jtag-debugging/index.html |
| Console / Monitor | 搜 `idf.py monitor` |
| Fatal Errors / Core Dump | API Guides 索引 |
| OpenOCD Espressif | 随 IDF tools 安装说明 |

## 最佳实践或坑

- 先区分「看门狗复位 / 栈溢出 / 非法访问 / 供电褐联」。
- `printf` 重入与 ISR 日志可导致死锁假象。
- 量产固件关掉冗余调试日志与 console RX 命令面。

## 参考链接

- [API Guides 索引](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/index.html)
- 检索：`esp_backtrace_print`、`heap tracing ESP-IDF`
