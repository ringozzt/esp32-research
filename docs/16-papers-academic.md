# 16 · 论文与学术方向（检索指南）

## 概述

ESP32 在学术与工业研究中常见于：**物联网安全**、**低功耗传感**、**无线测量 / CSI**、**Mesh 组网**、**TinyML / 边缘推理**、**智能家居互操作**。本篇**不编造论文标题、作者或会议录用结果**。下列为可复现的**检索关键词**与**常见发表 venue 类型**；具体文献请用 Google Scholar / IEEE Xplore / ACM DL / 语义学者自行核验。

## 关键点（方向地图）

| 方向 | 检索关键词（英文为主） | 常见 venue 类型 |
| --- | --- | --- |
| IoT 安全 / 固件 | `ESP32 secure boot` `IoT firmware analysis` `UART attack IoT` | IEEE IoT Journal、ACSAC、RAID、WOOT |
| 侧信道 / 射频 | `ESP32 side channel` `Wi-Fi CSI sensing` | IEEE S&P 工坊、IMWUT |
| 低功耗 | `ESP32 deep sleep energy` `ULP sensor node` | SenSys / IPSN 海报与短文 |
| Mesh / 协议 | `ESP-NOW performance` `Wi-Fi mesh IoT` | 通信类会议 |
| TinyML | `TinyML ESP32` `TensorFlow Lite Micro ESP32-S3` `ESP-DL` | TinyML Summit、NeurIPS 工坊、EdgeSys |
| Matter / Thread | `Matter protocol security` `Thread border router` | 网络/安全工坊 |

## 代表项目 / 资源（非论文，但是学术常用基线）

| 资源 | 链接 |
| --- | --- |
| ESP-IDF 安全文档 | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/security.html |
| esp-tflite-micro | https://github.com/espressif/esp-tflite-micro |
| Wi-Fi CSI（IDF 能力，研究常用） | 文档搜 `CSI` |

## 最佳实践或坑

- 引用前打开 PDF：**平台是 ESP8266 还是 ESP32、哪一代硅**常被摘要省略。
- 性能表注意主频、PSRAM、是否 ESP-NN、是否 Wi-Fi 同开。
- 预印本与同行评议区分标注。

## 参考链接

- Scholar 示例查询：`"ESP32" "secure boot"`、`"ESP32-S3" "person detection"`、`"ESP-NOW" latency`
- 中文检索：`ESP32 侧信道`、`ESP32 CSI 感知`、`嵌入式 TinyML`
