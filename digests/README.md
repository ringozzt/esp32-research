# 每日 ESP32 摘要（digests）

本目录存放**每日**从公开来源抓取的 ESP32 / ESP-IDF / Matter / 边缘 AI / 开源固件相关更新摘要。

## 文件命名

```
YYYY-MM-DD.md
```

示例：`2026-10-23.md`。时区按 **Asia/Shanghai（UTC+8）** 的日历日归档。

## 每篇结构

请复制 [_TEMPLATE.md](_TEMPLATE.md) 填写，至少包含：

1. **元信息**：日期、抓取窗口、来源列表  
2. **今日要点**：3–8 条 bullet  
3. **表格**：仓库 / 论文 / 公告名 | 类型 | 简述 | 链接 | 核实状态  
4. **与本仓库主线交叉**：若与芯片选型、IDF、安全、OTA、Matter、AI 等相关，注明并链到 `docs/`  
5. **未核实项**：单方说法、未复核 stars/论文单独列出

## 范围提示

**纳入：** Espressif 官方公告与文档更新、ESP-IDF / Arduino-ESP32 / MicroPython 发布、ESPHome / Tasmota / Home Assistant 相关变更、Matter / Thread / Zigbee、安全（Secure Boot / 加密 / CVE）、边缘 AI（ESP-DL / WHO / TFLite）、值得跟进的开源硬件/固件仓库、可核验的学术论文或会议摘要。

**不纳入：** 与 ESP32 无关的热度仓库；无法核验的「某某论文」「某某 stars」传闻。

## 与主语料关系

`docs/` 是相对稳定的专题层；`digests/` 是**增量层**，用来发现新芯片修订、新组件、新最佳实践，再择优回写专题。
