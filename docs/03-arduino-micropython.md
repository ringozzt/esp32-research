# 03 · Arduino-ESP32 vs ESP-IDF vs MicroPython / CircuitPython

## 概述

同一颗硅片上常见四条软件路径：**ESP-IDF**、**Arduino-ESP32**、**MicroPython**、**CircuitPython**。选择取决于上市时间、团队技能、是否需要最新无线/安全特性，以及 RAM/Flash 预算。

## 关键点

| 路径 | 适合 | 代价 |
| --- | --- | --- |
| ESP-IDF | 量产、安全、细粒度无线/电源 | 学习曲线、CMake |
| Arduino-ESP32 | 快速原型、第三方库 | 可能落后 IDF 新特性；内存更紧 |
| MicroPython | 脚本化、教学 | 性能/实时性弱于原生 |
| CircuitPython | 教育、Adafruit 生态 | 板级支持子集 |

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Arduino-ESP32 | https://github.com/espressif/arduino-esp32 |
| Arduino-ESP32 文档 | https://docs.espressif.com/projects/arduino-esp32/en/latest/ |
| MicroPython | https://github.com/micropython/micropython （`ports/esp32`） |
| MicroPython ESP32 文档 | https://docs.micropython.org/en/latest/esp32/quickref.html |
| CircuitPython | https://github.com/adafruit/circuitpython |
| PlatformIO Espressif32 | https://docs.platformio.org/en/latest/platforms/espressif32.html |

## 最佳实践或坑

- **要 Matter / 新 C6 / Secure Boot 量产流**：优先 IDF 或明确支持的固件发行版。
- Arduino 可作为 **IDF component** 逐步下沉。
- MicroPython：固件必须与芯片匹配；冻结模块与 OTA 要单独设计。

## 参考链接

- [ESPHome ESP32 平台](https://esphome.io/components/esp32/)
- 检索：`arduino as esp-idf component`、`micropython esp32s3 octal psram`
