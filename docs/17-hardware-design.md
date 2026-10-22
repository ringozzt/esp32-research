# 17 · 硬件设计最佳实践（天线、电源、Flash、PSRAM）

## 概述

软件再稳，射频与电源布线翻车会表现为「偶发断连、吞吐差、深睡电流大、Flash 校验失败」。优先：**官方模组（已认证）** > 模组+载板 > 完全自画芯片+天线（需认证预算）。

## 关键点

- **天线**：模组板载天线净空；外置天线匹配与 SMA 座接地；金属壳开窗。
- **电源**：峰值电流（Wi-Fi 发射）、去耦电容靠近电源脚、磁珠分区模拟/数字。
- **Flash/PSRAM**：走线短、等长/参考层完整；Octal 更敏感；跟乐鑫硬件设计指南。
- **Strapping**：上电电平决定启动模式；复用外设时加注。
- **ESD / 浪涌**：USB、以太网 RJ45、RS-485 口。
- **热**：封闭外壳与 PA 发热。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| 乐鑫模组与硬件文档入口 | https://www.espressif.com/en/products |
| 各芯片 Hardware Design Guidelines | 在 espressif.com 文档中心搜芯片名 + `Hardware Design` |
| 开发板原理图 | 各 DevKit 产品页 |

## 最佳实践或坑

- 自画 ESP32-S3 + Octal PSRAM：几乎必须复刻官方推荐电路。
- ADC 脚先当射频/天线附近时噪声巨大。
- 电池+USB 同时插入的电源路径（理想二极管/充电 IC）必须明确。
- 认证：模组「移植」条件与重新测认证的边界问认证实验室，勿信二手群传说。

## 参考链接

- 检索：`ESP32 hardware design guidelines PDF`、`ESP32-S3 Octal PSRAM design`
