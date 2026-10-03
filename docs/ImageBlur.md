# 图像平滑降噪 (ImageBlur)

## 1. 功能概述
为图像提供专业滤波平滑与降噪处理。包含高斯平滑滤波（GaussianBlur）、中值滤波（MedianFilter）以及方框均值滤波（BoxFilter）。

## 2. 核心特性
- **消除噪点纹理**：在 OCR 识别前消除扫描件底纹噪点；在 Canny 边缘检测前抑制高频噪声。
- **保护边缘的中值滤波**：中值滤波是去除椒盐噪点（Salt-and-pepper noise）与扫描仪脏点的利器，在去除噪点的同时完整保留文本笔画边缘锐利度。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 源图像 |
| `filter_type` | `MixedType` | `"Gaussian"` | 滤波器类型：`Gaussian`（高斯）、`Median`（中值）、`Box`（均值） |
| `radius` | `MixedType` | `2.0` | 滤波半径或高斯标准差 Sigma |
| `output_path` | `MixedType` | `""` | 可选保存路径 |

## 4. 输出
- 返回平滑降噪后的图像对象 `Image`。
