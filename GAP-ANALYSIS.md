# 缺口分析（GAP-ANALYSIS）

**语料：** ESP32 中文调研（本仓库）  
**基线日期：** 2026-10-22（Asia/Shanghai）  
**方法：** 对照乐鑫公开产品线、ESP-IDF stable 文档结构、主流开源固件；不声称穷尽所有 PN 或论文。

## 已覆盖

| 区块 | 内容 |
| --- | --- |
| 索引 | README 芯片速查表 + 25 篇专题导航 |
| 硅片 | 经典 / S2 / S3 / C2 / C3 / C5 / C6 / C61 / H2 / H4 / P4 / S31 等（细参指向官方） |
| SDK | IDF 构建、Arduino / MicroPython / CircuitPython、FreeRTOS |
| 连接 | Wi-Fi/BLE/Thread/Zigbee/Matter、ESP-NOW/Mesh、Ethernet、LoRa/蜂窝外挂 |
| 系统 | 外设、功耗、安全、OTA、USB、调试、CI |
| 应用 | Camera/LVGL、边缘 AI、智能家居栈、开源项目、社区、坑清单 |
| 学术 | 检索关键词与 venue 类型（无伪造题录） |
| 增量 | `digests/` 模板与吸收路线（24） |

## 已知缺口

| 缺口 | 说明 | 建议 |
| --- | --- | --- |
| 逐 PN 电气参数 | 未复制 datasheet 全表 | 选型时链到产品页 PDF |
| IDF 小版本差异 | 以 stable 概念为准，未锁某一 patch | digests 跟踪 Releases |
| 认证实操 | CE/FCC/SRRC/Matter 认证流程未展开 | 新增专题或外链实验室 |
| HomeKit ADK 细节 | 侧重 Matter 路径 | 若项目需要再补 |
| 中文社区深度帖 | 未系统归档论坛长帖 | digests 摘录 + 核实 |
| 论文精读 | 仅关键词 | 选定方向后按篇写 `docs/paper-*.md` |
| Zephyr/NuttX 深度 | 仅入口级 | 按需扩写 |
| 安全 CVE 编年 | 无独立时间线 | 与安全日报交叉时补 |
| 参考设计 BOM | 无 | 链官方 DevKit 原理图 |
| 性能测试基准 | 无自测数据 | 禁止抄无来源数字 |

## 建议的下一批评题

1. ESP-IDF v5.x → v6.x 迁移备忘（等 digests 积累）  
2. Thread Border Router 参考设计对照（S3+H2 / 官方模组）  
3. ESP32-C5 双频实测笔记（需硬件）  
4. Secure manufacturing 夹具与 eFuse 工站 checklist  
5. ESPHome native IDF toolchain 变更对二次开发的影响  
6. 按垂直场景：电表 / 门锁 / 摄像头门铃 的选型模板  

## 刻意不做的事

- 不编造 GitHub stars、论文标题、未公开路线图  
- 不把营销幻灯片性能数字写成事实  
- 不在本阶段创建 GitHub remote 或定时任务（由父流程处理）  
