# 12 · 边缘 AI：ESP-DL / ESP-WHO / TFLite Micro / AFE

## 概述

乐鑫边缘推理主路径：**ESP-DL**（自有模型格式与算子库）→ 应用框架 **ESP-WHO**（人脸/行人/二维码等示例）；以及 **esp-tflite-micro**（TensorFlow Lite Micro + **ESP-NN** 加速）。语音前端常见 **ESP-SR / AFE**（唤醒、降噪等，以官方 SR 文档为准）。S3/P4 更适合视觉；小模型也可在 C3 等尝试，但要接受帧率与内存限制。

## 关键点

- 模型来源：官方 zoo / 自己量化；对齐输入尺寸与预处理。
- ESP-NN：显著加速部分 TFLite 算子（官方仓库 README 有对照表，**数字随版本/主频变化，引用时打开当前 README**）。
- 内存：PSRAM、模型放 Flash mmap、双缓冲。
- 许可与隐私：人脸识别产品合规另议。

## 代表项目 / 资源

| 资源 | 链接 |
| --- | --- |
| ESP-DL | https://github.com/espressif/esp-dl |
| ESP-WHO | https://github.com/espressif/esp-who |
| esp-tflite-micro | https://github.com/espressif/esp-tflite-micro |
| ESP-NN | https://github.com/espressif/esp-nn |
| ESP-SR | https://github.com/espressif/esp-sr |

## 最佳实践或坑

- 先跑通官方 example 再换模型；核对支持的 IDF 版本（WHO README 列出支持的 release）。
- 不要把桌面 GPU 论文指标直接当成片上可达指标。
- 学术对比：自行检索会议论文，本篇不编造标题——关键词见下。

## 参考链接

- 检索论文/方向关键词：`ESP32 tinyML`、`MCUNet`、`TensorFlow Lite Micro person detection`、`on-device face detection quantized`
- [ESP-VISION AI Inference](https://docs.espressif.com/projects/esp-vision/en/latest/esp32p4/concepts/ai-inference.html)
