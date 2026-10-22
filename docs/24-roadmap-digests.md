# 24 · 仓库演进路线与 digests 机制

## 概述

主语料（`docs/`）追求**相对稳定的地图**；`digests/` 承接**每日增量**（新芯片 PN、IDF release、ESPHome/Tasmota 变更、CVE、可核验论文）。本篇约定如何吸收日报、何时升格为专题、何时只留链接。

## 关键点

1. **每日**：按 [digests/README.md](../digests/README.md) 产出 `YYYY-MM-DD.md`。  
2. **每周**：浏览未核实项；能交叉验证的链到对应 `docs/`。  
3. **升格条件**：同一主题在 digests 出现 ≥3 次，或影响选型/安全，则改专题或新增 `docs/25+`。  
4. **不升格**：一次性 demo、无法核验 stars/论文、纯营销稿。  
5. **GAP-ANALYSIS**：缺口关闭时更新 [GAP-ANALYSIS.md](../GAP-ANALYSIS.md)。

## 代表项目 / 资源

| 监控源（建议） | 链接 |
| --- | --- |
| esp-idf Releases | https://github.com/espressif/esp-idf/releases |
| Arduino-ESP32 Releases | https://github.com/espressif/arduino-esp32/releases |
| ESPHome Blog | https://esphome.io/blog/ |
| Tasmota Releases | https://github.com/arendst/Tasmota/releases |
| Espressif Developer Blog | https://developer.espressif.com/ |
| NVD / 乐鑫安全公告 | 检索 `Espressif security advisory` |

## 最佳实践或坑

- digests **禁止编造** stars 与论文；写「未核实」。  
- 中文摘要可对英文 changelog 意译，但保留原链接。  
- 大版本迁移（IDF v5→v6 等）单独开迁移笔记，勿只改一句 README。

## 参考链接

- 模板：[digests/_TEMPLATE.md](../digests/_TEMPLATE.md)
