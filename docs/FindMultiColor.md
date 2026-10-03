# 多点锚点找色 (FindMultiColor)

## 1. 功能概述
按“基准锚点 + 多个相对偏移点颜色”的几何拓扑结构进行匹配。借鉴大厂工业图色脚本标准，彻底解决动态复杂背景、文字无固定模板图但拥有特征色块拓扑的极致定位场景。

## 2. 核心特性
- **拓扑几何容抗**：即使背景颜色波动，只要特征色块之间的相对间距与色彩保持一致即可稳健命中。
- **紧凑特征描述**：支持工业标准描述串 `dx|dy|#HEX, dx|dy|#HEX...`。

## 3. 参数说明

| 属性名称 | 参数类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `image` | `MixedType` | - | 源图像路径或变量 |
| `anchor_color` | `MixedType` | `"#FFFFFF"` | 主点基准颜色（HEX `#RRGGBB` 或 RGB） |
| `offset_points` | `MixedType` | `"5,0,#FF0000\|0,5,#0000FF"` | 相对偏移点列表，格式 `dx,dy,#Color\|dx2,dy2,#Color2` |
| `tolerance` | `MixedType` | `15` | 偏色容差（0 ~ 255） |
| `search_region` | `MixedType` | `""` | 搜索 ROI 区域，留空全图检索（`x, y, w, h`） |
| `debug_save_path` | `MixedType` | `""` | 可选调试截图保存路径 |

## 4. 输出
- 返回主基准点绝对坐标 `Point(x, y)`。
