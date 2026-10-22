# 05 · Wi-Fi / BLE / Thread / Zigbee / Matter 能力地图

## 概述

无线能力**按芯片切割**，不是「ESP32 全家桶都有」。经典 ESP32：Wi-Fi 4 + BT Classic/BLE。S2：仅 Wi-Fi。S3：Wi-Fi + BLE 5。C3/C2：Wi-Fi + BLE。C6/C5：Wi-Fi 6（C5 双频）+ BLE + 802.15.4。H2：无 Wi-Fi，BLE + 802.15.4。P4：无片上射频。Matter 是应用层协议，可跑在 Wi-Fi 或 Thread 上（见 [20](20-matter-smarthome.md)）。

## 关键点

| 技术 | 典型芯片 | IDF / 方案入口 |
| --- | --- | --- |
| Wi-Fi STA/AP/Scavenging | 多数带 Wi-Fi 的系列 | Wi-Fi Driver API Guide |
| BLE / BluFi | S3、C 系、经典 32、H 系 | Bluedroid / NimBLE 组件 |
| Thread / OpenThread | C6、C5、H2 等 | OpenThread API Guide |
| Zigbee | 同上 802.15.4 芯片 | esp-zigbee-sdk |
| Matter | Wi-Fi 或 Thread 端点 | esp-matter |
| 共存 | 同芯片多协议 | RF Coexistence 文档 |

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Wi-Fi Driver 指南 | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/wifi.html |
| OpenThread | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/openthread.html |
| esp-matter | https://github.com/espressif/esp-matter |
| esp-zigbee-sdk | https://github.com/espressif/esp-zigbee-sdk |
| RF Coexistence | 在 API Guides 中搜索 `RF Coexistence` |

## 最佳实践或坑

- **先查芯片矩阵再开 Matter-over-Thread**：经典 ESP32 / S3  alone 不能当 Thread radio。
- Wi-Fi 与 BLE 同开时注意共存配置与天线；吞吐与延迟预期要实测。
- 认证（CE/FCC/SRRC）按**模组**还是自画天线方案路径完全不同。

## 参考链接

- [SoC 产品页](https://www.espressif.com/en/products/socs)
- 检索：`esp-matter thread border router`、`ESP32-C6 Wi-Fi 6`
