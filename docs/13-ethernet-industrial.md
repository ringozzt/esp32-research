# 13 · Ethernet / PoE / 工业向

## 概述

部分 **经典 ESP32** 与 **ESP32-P4** 等提供 Ethernet MAC（具体以 datasheet 为准），外挂 PHY 做有线联网；工业场景常见 **TWAI/CAN**、RS-485（UART+收发器）、Modbus 协议栈（应用层）。PoE 需独立 PD 电源方案，不是 SoC 内置功能。ESP32-S31 等新品线对 RGMII 等能力以乐鑫公告与 ESPHome/IDF 发布说明为准。

## 关键点

- PHY：RMII 常见于经典 ESP32 参考设计；时序与 50 MHz clock 布线敏感。
- 有线优先场景：工厂、机柜、Wi-Fi 不稳定处。
- TWAI：ISO11898 收发器 + 终端电阻。
- 协议：Modbus TCP/RTU、MQTT over Ethernet 等。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Ethernet 驱动文档 | IDF 搜 `Ethernet`：https://docs.espressif.com/projects/esp-idf/en/stable/ |
| TWAI | Peripherals → TWAI |
| ESPHome Ethernet | https://esphome.io/components/ethernet.html |
| 乐鑫以太网相关示例 | esp-idf/examples 下 ethernet |

## 最佳实践或坑

- 隔离变压器、ESD、RJ45 外壳接地按安规来。
- PoE：热设计与 PD 芯片选型独立评审。
- 「工业」还需 EMC、看门狗、掉电保存、认证——芯片只是一部分。

## 参考链接

- 检索：`ESP32 RMII PHY`、`ESP32-P4 Ethernet`、`TWAI SN65HVD230`
