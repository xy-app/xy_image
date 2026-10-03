# 颜色空间转换 (CvtColor)

## 1. 功能概述
在不同色彩空间（RGB、BGR、灰度 GRAY、HSV、HLS）之间进行高精度转换。

## 2. 核心特性
- **标准色彩转换公式**：严格遵循 ITU-R BT.601 国际灰度转换标准权重（$Y = 0.299R + 0.587G + 0.114B$）。
- **HSV/HLS 色彩解耦**：将色调（Hue）、饱和度（Saturation）、明度（Value）与亮度（Lightness）分离，为后续光照无关的印章提取和颜色过滤提供基础。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 源图像 |
| `code` | `MixedType` | `"RGB2GRAY"` | 转换代码（`RGB2GRAY`, `GRAY2RGB`, `RGB2HSV`, `HSV2RGB`, `RGB2HLS`, `RGB2BGR`） |
| `output_path` | `MixedType` | `""` | 可选保存路径 |

## 4. 输出
- 返回转换后的图像对象 `Image`。
