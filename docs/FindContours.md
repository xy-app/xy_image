# 轮廓提取与多维过滤 (FindContours)

## 1. 功能概述
基于 Suzuki 拓扑轮廓跟踪算法提取二值图像中的物体外部几何边界轮廓，内置一站式面积（Area）与周长（Perimeter）去噪过滤。

## 2. 核心特性
- **内置面积/周长过滤网**：彻底告别冗余的 `FilterArea`、`FilterPerimeter` 等中间零碎算子，直接在提取阶段剔除微小尘埃噪点和巨大背景框。
- **目标直出**：自动计算提取各个轮廓的外接矩形列表，并直接定位面积最大目标的几何中心坐标 `Point`。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 二值输入图像 |
| `min_area` | `MixedType` | `50.0` | 最小轮廓面积阈值（过滤过小噪点） |
| `max_area` | `MixedType` | `1000000.0` | 最大轮廓面积阈值（过滤全图外框） |
| `min_perimeter` | `MixedType` | `0.0` | 最小周长阈值 |

## 4. 输出
- 返回合格轮廓数量（Number）。
- 上下文变量：
  - `contour_rects`：合格轮廓的外接矩形列表（`Vec<Rect>`）。
  - `largest_contour_center`：最大目标的几何中心坐标 `Point`。
