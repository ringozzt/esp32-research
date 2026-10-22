# 02 · ESP-IDF 架构与构建系统

## 概述

[ESP-IDF](https://github.com/espressif/esp-idf)（Espressif IoT Development Framework）是官方 C/C++ SDK：基于 **CMake + Ninja**，用 `idf.py` 统一配置、编译、烧录、监视。组件（component）模型把驱动、协议栈、应用拆成可复用单元；Kconfig/`menuconfig` 管理芯片与功能开关。稳定文档：https://docs.espressif.com/projects/esp-idf/en/stable/

## 关键点

- **工程结构**：根 `CMakeLists.txt` + `main/` + 可选 `components/`；依赖可用 Component Registry（`idf.py add-dependency`）。
- **构建**：`idf.py set-target esp32s3` → `menuconfig` → `build` → `flash monitor`。
- **分区表**：`partitions.csv` 定义 nvs / otadata / app 等；OTA 与加密强依赖正确分区。
- **版本策略**：量产跟 **stable**；追新功能可读 `latest`，并锁 commit。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| esp-idf 仓库 | https://github.com/espressif/esp-idf |
| 编程指南（stable） | https://docs.espressif.com/projects/esp-idf/en/stable/ |
| Build System | https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/build-system.html |
| Component Registry | https://components.espressif.com/ |

## 最佳实践或坑

- 安装路径避免空格、超长路径（Windows 尤其易踩）。
- **先 `set-target` 再写死 sdkconfig**，换芯片要清 build。
- 第三方组件注明兼容的 IDF 大版本；`sdkconfig.defaults` 纳入版本控制。

## 参考链接

- [API Guides 索引](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/index.html)
- [Versions 说明](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/versions.html)
