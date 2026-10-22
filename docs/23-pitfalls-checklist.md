# 23 · 常见陷阱与检查清单

## 概述

把重复踩坑收敛成清单，发布前当 gate。细节分散在各专题；此处为**可打印检查表**。

## 关键点（检查清单）

### 选型

- [ ] 无线需求（Wi-Fi 代数 / BLE / Thread / 无射频）与芯片矩阵一致  
- [ ] Flash/PSRAM 容量覆盖 UI/模型/OTA 双分区  
- [ ] 生命周期与供货（尤其经典 ESP32）

### 软件

- [ ] IDF/Arduino 版本锁定；`set-target` 正确  
- [ ] 分区表含 OTA；签名与加密策略明确  
- [ ] 任务栈、优先级、看门狗  
- [ ] Wi-Fi/BLE 共存与重连状态机

### 硬件

- [ ] Strapping 脚  
- [ ] 天线净空 / 模组认证路径  
- [ ] 峰值供电与电池内阻  
- [ ] USB ESD

### 安全

- [ ] 生产 Flash Encryption = Release  
- [ ] Secure Boot 私钥保管  
- [ ] OTA HTTPS + 签名  
- [ ] 调试口关闭策略

### 发布

- [ ] 真机电流与温升  
- [ ] 掉电/烂网 OTA 回滚  
- [ ] 日志不含密钥  

## 代表项目 / 资源

- 安全总览：https://docs.espressif.com/projects/esp-idf/en/stable/esp32/security/security.html  
- 硬件设计指南：乐鑫文档中心按芯片检索  

## 最佳实践或坑

- 「开发板能跑」≠「自绘板能过认证」。  
- 不要在未理解 eFuse 前在客户设备上试 Secure Boot。

## 参考链接

- 回到 [00 总览](00-overview-taxonomy.md) 按需跳转专题。
