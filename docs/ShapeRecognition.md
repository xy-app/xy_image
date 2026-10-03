# 几何形状识别与匹配 (ShapeRecognition)

## 1. 功能概述
结合了几何拓扑分类与形状特征比对（Hu 矩不变矩匹配），用于工业视觉中的工件形状检测、几何标记判定与分类识别。

## 2. 核心特性
- **自动几何分类**：
  - 基于圆度（Circularity = $4\pi \times \text{Area} / \text{Perimeter}^2$）识别正圆与椭圆。
  - 基于轮廓角点与外接矩形宽高比识别矩形、正方形与三角形。
- **目标形状比对**：通过比对轮廓的七个平移/旋转/缩放不变矩（Hu Moments），返回目标形状的匹配相似度。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 输入二值化图像或轮廓图（路径或变量） |
| `mode` | `MixedType` | `"GeometricClassify"` | 识别模式：`GeometricClassify`（几何分类）或 `TemplateMatch`（模板比对） |
| `target_shape` | `MixedType` | `"Circle"` | 目标形状：`Circle`（圆）、`Rectangle`（矩形）、`Triangle`（三角形）、`Polygon`（多边形） |
| `min_area` | `MixedType` | `50.0` | 最小形状面积过滤阈值 |

## 4. 输出
- 返回检测到的主要形状分类名称（String，如 `"Circle"`, `"Rectangle"`, `"Unknown"`）。
- 上下文变量：
  - `detected_shapes`：包含每个检测物体的形状名称、中心坐标与置信度元组列表。
  - `matched_shape_center`：首个命中的目标形状几何中心坐标 `Point`。
