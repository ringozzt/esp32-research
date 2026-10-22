# 09 · OTA 更新模式

## 概述

ESP-IDF 用**双（或多）应用分区** + `otadata` 做 A/B 升级；推荐 **ESP HTTPS OTA** 经 TLS 拉镜像。启用 Secure Boot 时服务器侧托管**已签名**镜像；启用 Flash Encryption 时设备端写入路径负责密文，服务器不必预加密应用镜像（见 Security Overview 的 Secure OTA 小节）。

## 关键点

- **分区**：至少两个 `app` 分区，尺寸盖住未来版本。
- **流程**：下载 → 校验 → 设 boot 分区 → 重启 → 应用确认（`esp_ota_mark_app_valid`）防变砖。
- **回滚**：新固件未确认则回退旧槽。
- **Anti-rollback**：与 eFuse 安全版本联动。
- **差分 / 压缩**：可用第三方或官方示例方案，但要评估验签覆盖范围。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| OTA 更新 API 指南 | 文档搜 `OTA Update`：https://docs.espressif.com/projects/esp-idf/en/stable/ |
| ESP HTTPS OTA | 搜 `ESP HTTPS OTA` |
| Security Overview · Secure OTA | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/security.html |
| 分区表 | 搜 `Partition Tables` |

## 最佳实践或坑

- 强制 **HTTPS + 证书钉扎或可信 CA**；勿明文 HTTP OTA。
- 固件签名与 Secure Boot 密钥体系一致；测试用 key 与生产 key 隔离。
- 断电：选择支持断点/校验的设计；更新窗口避开高发操作。
- Arduino/`Update` 库与 IDF OTA 概念类似但 API 不同，混用文档会踩坑。

## 参考链接

- 检索：`esp_https_ota`、`esp_ota_mark_app_valid_cancel_rollback`
