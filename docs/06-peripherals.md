# 06 · 外设：GPIO / ADC / DAC / I2C / SPI / UART / RMT / TWAI / LEDC / Touch

## 概述

ESP-IDF 通过 **GPIO Matrix**（多数系列）把外设信号灵活映射到引脚；各系列外设实例数、ADC 线性度、是否保留 DAC/Touch 不同。驱动层常用 `esp_driver_*` 新驱动（IDF v5+）替代旧 `driver/` 遗留 API——新项目优先新驱动。

## 关键点

| 外设 | 典型用途 | 注意 |
| --- | --- | --- |
| GPIO | 输入输出、中断 | strapping 脚、下载模式脚 |
| ADC | 传感器、电池分压 | 衰减、校准、非线性；勿当精密表 |
| DAC | 音频/模拟出 | 多见于经典/S2；S3 等可能无 |
| I2C | 传感器、触摸屏 | 上拉、时钟拉伸、多主机 |
| SPI | Flash/屏/SD | DMA、与片内 Flash 总线冲突 |
| UART | 调试、模组 | 波特率、流控、USB-Serial-JTAG 替代 |
| RMT | 红外、WS2812 | 时序外设首选 |
| TWAI | CAN 2.0 | 需收发器；工业向 |
| LEDC | PWM 灯/电机 | 高分辨率定时 |
| Touch | 触摸按键 | 湿度/布局敏感；系列支持不一 |

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| 外设 API（按 target） | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/index.html |
| GPIO & RTC GPIO | 同上树内 GPIO 页 |
| TWAI | 同上树内 TWAI 页 |
| RMT | 同上树内 RMT 页 |

## 最佳实践或坑

- **先读该芯片 Technical Reference / datasheet 引脚表**，再抄别的开发板原理图。
- ADC：用校准 API；电池监测建议外部分压 + 电容，注意 Wi-Fi 发射时噪声。
- WS2812 用 RMT 或专用库，忌在中断里 bit-bang 过久。
- 复用 USB-Serial-JTAG 的芯片：调试口与 UART0 关系要搞清。

## 参考链接

- 检索：`esp_driver_gpio`、`ADC continuous mode ESP-IDF`、`RMT WS2812`
