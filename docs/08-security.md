# 08 · 安全：Secure Boot、Flash 加密、NVS、TEE

## 概述

量产设备建议组合：**Secure Boot v2**（验签启动链）+ **Flash Encryption**（Release 模式）+ 安全 OTA + 密钥与 NVS 加密。eFuse 一次性烧写，**顺序与模式选错可能变砖或无法再明文下载**。官方总览：Security Overview。

## 关键点

| 能力 | 作用 | 注意 |
| --- | --- | --- |
| Secure Boot v2 | 只跑已签名镜像 | 私钥离线保管；可多 key |
| Flash Encryption | 片外 Flash 密文 | 生产用 Release；Development 仅实验室 |
| NVS Encryption | 保护键值分区 | 与 Flash 加密密钥体系协同 |
| Secure OTA | HTTPS + 签名镜像 | 见 [09](09-ota.md) |
| Anti-rollback | eFuse 安全版本 | 防降级 |
| JTAG | 安全功能开启后通常禁用 | 调试窗口要提前规划 |
| TEE | 部分新平台/文档中的可信执行向能力 | 以当前 IDF target 文档为准，勿假设经典 ESP32 有同等模型 |

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| Security Overview | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/security.html |
| Flash Encryption | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/flash-encryption.html |
| Secure Boot v2 | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/secure-boot-v2.html |
| FreeRTOS 参考上的安全步骤示例 | https://github.com/FreeRTOS/iot-reference-esp32/blob/main/UseSecurityFeatures.md |

## 最佳实践或坑

- **先在报废板走完整加密+安全启动流水线**，再动产线夹具。
- Flash Encryption + Secure Boot 一起用，缓解 TOCTOU 换 Flash 攻击（官方亦建议组合）。
- 私钥进 CI 需 HSM/受限 runner；不要进公开仓库。
- 「加密了就能防一切」不成立：侧信道、调试接口、云端凭据仍是常见突破口。

## 参考链接

- 检索：`espsecure.py`、`idf.py secure-`、`NVS encryption ESP-IDF`、`ESP-TEE`
