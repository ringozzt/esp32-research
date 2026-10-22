# 14 · USB OTG / TinyUSB / USB-Serial-JTAG

## 概述

**ESP32-S2/S3** 等提供 USB OTG，可走 **TinyUSB** 做 HID、MSC、CDC 等设备（或主机，视支持）。许多新芯片集成 **USB-Serial-JTAG**，免外部 USB-UART 即可下载与日志。P4 等平台有更丰富的高速 USB 能力，以该 target 文档为准。

## 关键点

- Device：CDC 虚拟串口、MSC 暴露 FatFS、HID 键盘鼠标。
- 下载模式：USB-Serial-JTAG vs UART0 strapping。
- TinyUSB 作为 IDF 组件维护；示例在 esp-idf examples。
- 与 JTAG 调试：安全 eFuse 会影响可用性（见 [08](08-security.md)）。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| USB 相关文档 | IDF 搜 `USB OTG` / `TinyUSB` / `USB Serial/JTAG` |
| TinyUSB | https://github.com/hathach/tinyusb （上游；乐鑫 fork/组件以 IDF 为准） |
| Arduino-ESP32 USB | https://docs.espressif.com/projects/arduino-esp32/en/latest/ |

## 最佳实践或坑

- Windows 驱动/组合设备枚举问题：先在 Linux/macOS 验证。
- 自绘板：ESD、差分等长、D+/D- 互换是高频硬件坑。
- 量产烧录夹具协议与 USB 下载模式要提前与工厂对齐。

## 参考链接

- 检索：`esp_tinyusb`、`USB_SERIAL_JTAG`、`ESP32-S3 USB HID`
