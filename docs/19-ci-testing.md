# 19 · CI / 单元测试 / Host 测试

## 概述

ESP-IDF 支持 **目标板上 Unity 单元测试**与 **Linux host 测试**（部分组件），并可用 Docker / GitHub Actions 做编译矩阵（多 target、多 IDF 版本）。硬件在环（HIL）需自备 runner 与串口继电器；不要假设官方托管免费硬件农场。

## 关键点

- `idf.py` 构建矩阵：esp32 / s3 / c3 / c6…
- Unit Testing on ESP32 / on Linux：见官方 API Guides。
- pytest 嵌入式扩展：乐鑫与社区方案并存，选一种固化。
- 质量门禁：format、clang-tidy（若启用）、sdkconfig 一致性、签名校验脚本。
- OTA/安全：CI 用测试密钥；生产密钥隔离。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Unit Testing in ESP32 | 文档搜 `Unit Testing`：https://docs.espressif.com/projects/esp-idf/en/stable/ |
| Unit Testing on Linux | API Guides 索引中的对应条目 |
| IDF Docker 镜像说明 | 搜 `ESP-IDF Docker` |
| GitHub Actions + esp-idf 示例 | 检索社区 workflow（核验后使用） |

## 最佳实践或坑

- 锁定 IDF 版本与工具链版本文件，避免「周五绿灯、周一红灯」。
- 板级测试 flaky：电源、Wi-Fi 环境、串口占用要隔离。
- 不要把真实家中 MQTT 密码写进 CI 日志。

## 参考链接

- [Reproducible Builds 指南](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/reproducible-builds.html)（若当前 stable 仍收录）
- 检索：`esp-idf pytest embedded`、`qemu esp32`（若使用模拟）
