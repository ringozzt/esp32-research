# 21 · LoRa / 蜂窝 / 外挂无线电

## 概述

多数 ESP32 **片上没有 LoRa 或蜂窝调制解调器**。常见做法：SPI/UART 外挂 **SX127x / SX126x LoRa**、**LTE-M/NB-IoT/4G USB 或 UART 模组**、**GPS** 等。ESP32 负责应用、Wi-Fi 配置与协议桥接。部分乐鑫模组产品线组合「ESP + 其它连接」以官方模组目录为准。

## 关键点

- LoRa：区域频段合规（CN470 / EU868 / US915 等）、占空比、天线。
- 蜂窝：AT 指令、功耗（PSM/eDRX）、SIM、天线隔离。
- 与 Wi-Fi 天线共存：隔离度与噪声。
- 网关 vs 节点角色不同。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Arduino-LoRa 等社区库 | 检索 `sandeepmistry/arduino-LoRa`（经典，维护状态自行评估） |
| RadioLib | https://github.com/jgromes/RadioLib |
| ESPHome LoRa / SX126x 组件 | https://esphome.io/ 站内搜 |
| 蜂窝模组厂商文档 | 按模组型号（Quectel/SIMCom 等） |

## 最佳实践或坑

- **合规**：发射功率与频段未认证不要外售。
- 供电：LTE 峰值电流远超 Wi-Fi，电池内阻不足会掉线复位。
- 软件许可：部分蜂窝协议栈闭源，只拿到 AT 透传。

## 参考链接

- 检索：`ESP32 SX1262`、`ESP32 LTE modem AT`、`LoRaWAN LMIC ESP32`
