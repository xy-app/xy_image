# 连通域与斑点分析 (BlobAnalysis)

## 1. 功能概述
工业级连通域标记（Connected Components Labeling）与斑点特征统计分析。合并了旧有的 `ConnectedComponents` 与 `BlobDetect` 碎片功能。

## 2. 核心特性
- **两趟扫描连通域算法**：支持 4-邻域与 8-邻域连通性，快速分割互不连通的前景斑点块。
- **全要素工业统计**：自动统计斑点总数，计算每个斑点的精确面积（像素点数）、水平垂直外接包围盒 `Rect` 以及重心质心坐标 `(cx, cy)`。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 二值灰度图像 |
| `connectivity` | `MixedType` | `"8"` | 连通邻域模式：`"8"` 或 `"4"` |
| `min_area` | `MixedType` | `20` | 最小斑点面积阈值（过滤微小噪点） |
| `max_area` | `MixedType` | `1000000` | 最大斑点面积阈值 |

## 4. 输出
- 返回符合条件的斑点总数（Number）。
- 上下文变量：
  - `blob_bounding_boxes`：斑点外接矩形列表（`Vec<Rect>`）。
  - `blob_centroids`：斑点质心点位列表（`Vec<Point>`）。
