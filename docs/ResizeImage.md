# 图像尺寸缩放 (ResizeImage)

## 1. 功能概述
对图像进行缩放放大或缩小，支持按目标像素分辨率（Dimensions）或缩放系数（Scale Factor）。

## 2. 核心特性
- **等比例保持**：可开启 `keep_aspect_ratio`，以最大内接比例缩放，防止图像扭曲形变。
- **高质量插值**：采用 Lanczos3 / Triangle 双线性平滑重采样，保证图像缩放后的文字边缘清晰度。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 源图像 |
| `size` | `MixedType` | `"800, 600"` | 目标尺寸（`'w, h'` 或缩放比 `'0.5'`） |
| `mode` | `MixedType` | `"dimensions"` | 缩放模式：`dimensions`（指定像素宽高）或 `scale`（指定倍率） |
| `keep_aspect_ratio` | `MixedType` | `1` | 是否保持原始宽高比（`1` 是，`0` 否） |
| `output_path` | `MixedType` | `""` | 可选保存路径，留空返回内存图像 |

## 4. 输出
- 返回缩放后的图像对象 `Image`。
