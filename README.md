# 🖼️ 官方计算机视觉与图像处理套件 (Computer Vision & Image Suite)

[![Plugin Version](https://img.shields.io/badge/version-0.50.5-blue.svg)](manifest.json)
[![Group](https://img.shields.io/badge/group-Image-teal.svg)](#)
[![Platform](https://img.shields.io/badge/platform-All-green.svg)](#)
[![License](https://img.shields.io/badge/license-Freeware-brightgreen.svg)](#)

工业级轻量高性能机器视觉与图像算子套件。专为自动化测试、RPA 界面定位、智能打靶、工业缺陷质检与复杂视觉预处理设计，提供纳秒/微秒级响应的像素拾色、抗 DPI 缩放 NCC 模板匹配、多点锚点几何找色、免 OCR 表格网格结构提取、自适应二值化以及形态学轮廓与连通域分析能力。

---

## 📖 简介 (Overview)

`xy_image` 采用高效自研图形计算流水线，兼备极高执行效率与内存安全性：
- **精准屏幕定位**：内置基于 NCC（归一化互相关）的多尺度粗精模板匹配（`MatchTemplate`），无惧系统 DPI 缩放与轻微环境波动。
- **高频界面状态感知**：微秒级单点拾色与指示灯状态校验（`GetPixelColor`）、带容差的多点几何拓扑特征找色（`FindMultiColor`）、单色块区域快速搜索（`FindColor`）。
- **专业图像前处理**：涵盖 RGB/BGR/HSV/灰度全能转换（`CvtColor`）、大津法与局部自适应二值化（`ImageThreshold`）、高斯/中值/方框平滑滤波（`ImageBlur`）、HSV 色彩区间提取（`ImageInRange`）以及形态学开闭运算（`ImageMorphology`）。
- **几何与轮廓分析**：连通域/斑点缺陷统计（`BlobAnalysis`）、边缘追踪与多维过滤（`FindContours`）、多边形/圆形/矩形拓扑分类（`ShapeRecognition`）。
- **业务场景赋能**：无需部署 OCR 即可利用形态学网格线拓扑重构表格行列矩阵（`TableGridDetect`），以及自动化页面变动对比（`ImageComparison`）。

---

## ✨ 核心特性 (Features)

- **高性能工业级自研核心**：零复杂环境依赖，开箱即用，高并发低开销。
- **多尺度抗 DPI 找图**：NCC 模板匹配支持 `multi_scale` 粗精搜索，自适应屏幕缩放与高分屏定位。
- **抗动态背景找色体系**：多点找色支持 `主点色 + 相对偏移拓扑矩阵`，完美解决无图界面或背景动态干扰下的按键定位难题。
- **表格免 OCR 结构提取**：形态学横纵线滤波直接切分表格单元格坐标矩形矩阵，快速赋能表单抓取。
- **全流程视觉前处理**：缩放、正交旋转与镜像翻转、HSV/RGB 空间掩码抠图、大津法/局部积分自适应黑白二值化一应俱全。

---

## 🛠️ 动作指令全景速查 (Action Catalog)

| 动作标识 (Tag) | 功能名称 | 描述 | 输出类型 |
| :--- | :--- | :--- | :--- |
| `MatchTemplate` | 模板匹配定位 | 基于 NCC 归一化互相关在画面中搜索目标图，支持多尺度 DPI 适应与 ROI | `Point` |
| `FindMultiColor` | 多点锚点找色 | 以主点色为基准，比对多点相对几何拓扑色值，强抗动态背景 | `Point` |
| `FindColor` | 区域找色与色块定位 | 区域搜索目标色值，支持容差、首个匹配点或连通色块质心定位 | `Point` |
| `GetPixelColor` | 像素拾色与状态判定 | 读取指定像素 HEX 颜色值，微秒级判定指示灯或按钮激活状态 | `string` |
| `ImageComparison` | 图像比对与变动分析 | 比对图像视觉相似度 (0.0~1.0)，计算变动比例并高亮标记差异区域 | `real` |
| `TableGridDetect` | 表格网格检测与提取 | 提取横纵线并分割单元格，免 OCR 输出表格行列坐标矩阵与尺寸 | `TableGridResult` |
| `ImageThreshold` | 智能图像二值化 | 固定阈值、Otsu 大津全局最佳阈值与局部积分自适应二值化 | `Image` |
| `ImageInRange` | 颜色区间掩码提取 | 在 HSV/RGB 空间根据上下限提取掩码（提取印章、特殊标记与滤色） | `Image` |
| `ImageMorphology` | 形态学操作 | 开运算去噪、闭运算填孔桥接、膨胀加粗与腐蚀细化 | `Image` |
| `BlobAnalysis` | 连通域与斑点分析 | 统计独立连通域斑点数量、面积、外接矩形与质心（缺陷质检与计数） | `Point` |
| `FindContours` | 轮廓提取与多维过滤 | 提取几何外轮廓，内置面积与周长去噪过滤，输出中心点与矩形 | `Point` |
| `ShapeRecognition` | 几何形状识别与匹配 | 识别圆形、矩形、三角形或多边形拓扑，或基于 Hu 矩比对形状 | `string` |
| `ImageBlur` | 图像平滑降噪 | 高斯滤波、中值滤波（椒盐去噪）与方框均值滤波 | `Image` |
| `CropImage` | 图像精确裁剪 | 按矩形坐标或中心锚点截取局部 ROI 区域，带越界保护 | `Image` |
| `ResizeImage` | 图像尺寸缩放 | 指定绝对宽高像素或按比例因子缩放，支持锁定长宽比 | `Image` |
| `ImageRotate` | 图像旋转与翻转 | 90/180/270 度顺时针无损正交旋转及水平/垂直镜像翻转 | `Image` |
| `CvtColor` | 颜色空间转换 | RGB、BGR、灰度、HSV、HLS 之间高精度色彩空间转换 | `Image` |

---

## 📚 详细参数说明与参考 (Detailed Reference)

### 1. 目标定位与屏幕找图找色 (Screen Automation & Matching)

#### `MatchTemplate` - 模板匹配定位
在源画面中利用 NCC 算法定位模板图坐标。

- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设推荐值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `target` | 模板小图路径或变量 | `string` | `""` | - | 待查找的目标特征小图 |
  | `source` | 源大图路径或变量 | `string` | `""` | - | 被检索的源大图或全屏截图 |
  | `precision` | 匹配精度阈值 (0.0~1.0) | `real` | `0.8` | `0.7`, `0.8`, `0.9`, `0.95` | 归一化互相关置信度门限 |
  | `search_region` | 搜索区域 ROI | `string` | `""` | - | 格式为 `x, y, w, h`，限制在局部区域内检索 |
  | `multi_scale` | 多尺度搜索 (抗DPI) | `number` | `0` | `0`, `1` | `1` 为启用多尺度粗精匹配以自适应 DPI 缩放 |
  | `debug_save_path` | 调试截图保存路径 | `string` | `""` | - | 命中后在图上打框并持久化保存用于排错 |
- **输出类型：** `Point`（中心坐标点）

#### `FindMultiColor` - 多点锚点找色
以主点为基准比对周围多个偏移点的色彩几何拓扑。

- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- |
  | `image` | 源图像路径或变量 | `string` | `""` | 输入图像 |
  | `anchor_color` | 主点基准颜色 | `string` | `#FFFFFF` | 主参考点的目标 HEX 颜色值 |
  | `offset_points` | 相对偏移点列表 | `string` | `5,0,#FF0000\|0,5,#0000FF` | 格式: `dx,dy,#Color\|dx2,dy2,#Color2` |
  | `tolerance` | 偏色容差 (0~255) | `number` | `15` | 允许的各通道偏色波动范围 |
  | `search_region` | 搜索区域 ROI | `string` | `""` | 限制检索的局部区域 `x, y, w, h` |
  | `debug_save_path` | 调试截图路径 | `string` | `""` | 可视化标记保存路径 |
- **输出类型：** `Point`（主点坐标）

#### `FindColor` - 区域找色与色块定位
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设推荐值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `image` | 源图像路径或变量 | `string` | `""` | - | 输入图像 |
  | `color` | 目标颜色 | `string` | `#FF0000` | `#FF0000`, `#00FF00`, `#FFFFFF` | 目标 HEX 颜色 |
  | `tolerance` | 偏色容差 (0~255) | `number` | `10` | `0`, `5`, `10`, `20` | 偏色范围 |
  | `search_region` | 搜索区域 ROI | `string` | `""` | - | 局部区域 `x, y, w, h` |
  | `find_mode` | 定位模式 | `string` | `First` | `First`, `Centroid` | `First`: 首个像素点；`Centroid`: 色块质心 |
  | `debug_save_path` | 调试截图路径 | `string` | `""` | - | 调试标记保存路径 |
- **输出类型：** `Point`

#### `GetPixelColor` - 像素拾色与状态判定
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- |
  | `image` | 源图像路径或变量 | `string` | `""` | 输入图像 |
  | `coord` | 像素坐标 (x, y) | `string` | `0,0` | 目标坐标点 |
  | `expected_color` | 期望颜色 (可选校验) | `string` | `""` | 若提供则直接比对是否相等并返回判定 |
  | `tolerance` | 容差 (0~255) | `number` | `10` | 比对宽容度 |
- **输出类型：** `string`（拾取的颜色 Hex 字符串或比对结果）

---

### 2. 图像分割与前处理算子 (Image Preprocessing & Segmentation)

#### `ImageThreshold` - 智能图像二值化
- **算法模式 (`method`)**：
  - `Otsu`: 大津法全局最佳自适应阈值，适用于双峰直方图。
  - `Adaptive`: 局部积分自适应阈值，完美克服光照不均匀阴影。
  - `Fixed`: 手动固定阈值分割。
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设推荐值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `image` | 源图像路径或变量 | `string` | `""` | - | 待二值化图像 |
  | `method` | 二值化算法 | `string` | `Otsu` | `Otsu`, `Fixed`, `Adaptive` | 阈值分割策略 |
  | `thresh` | 固定阈值 (0~255) | `number` | `128` | `64`, `128`, `192` | 仅在 `Fixed` 模式生效 |
  | `block_radius` | 局部自适应半径 | `number` | `5` | `3`, `5`, `9`, `15` | 仅在 `Adaptive` 模式生效 |
  | `invert` | 反色反转 (0 否 / 1 是)| `number` | `0` | `0`, `1` | 黑白像素反转 |
  | `output_path` | 保存路径 (可选) | `string` | `""` | - | 存储结果路径 |
- **输出类型：** `Image`

#### `ImageInRange` - 颜色区间掩码提取
从彩色图像中提取特定颜色（如提取红色公章、滤除蓝底背景）。

- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设推荐值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `image` | 源图像路径或变量 | `string` | `""` | - | 输入图像 |
  | `lower_bound` | 下界三元组 | `string` | `0, 120, 70` | `0, 120, 70` | 颜色空间下限 |
  | `upper_bound` | 上界三元组 | `string` | `10, 255, 255` | `10, 255, 255` | 颜色空间上限 |
  | `color_space` | 色彩空间 (HSV / RGB) | `string` | `HSV` | `HSV`, `RGB` | 选定色彩空间 |
  | `output_path` | 保存路径 (可选) | `string` | `""` | - | 输出保存路径 |
- **输出类型：** `Image`

#### `ImageMorphology` - 形态学操作
- **参数：** `operation` (`Open` 开运算 / `Close` 闭运算 / `Dilate` 膨胀 / `Erode` 腐蚀)、`radius` (结构元素半径)、`norm` (`LInf` 方形 / `L1` 菱形)。
- **输出类型：** `Image`

#### `ImageBlur` - 图像平滑降噪
- **滤波类型 (`filter_type`)**：`Gaussian`（高斯模糊）、`Median`（中值滤波）、`Box`（均值滤波）。
- **参数：** `radius` (滤波半径/Sigma)。
- **输出类型：** `Image`

---

### 3. 几何分析、结构识别与差异对比 (Geometry & Analysis)

#### `TableGridDetect` - 表格网格检测与单元格提取
通过游程滤波提取表格线拓扑，实现免 OCR 的表格结构数字化。
- **输入参数：**
  - `image`: 包含网格线的数据表格图片。
- **输出类型：** `TableGridResult`（包含各单元格的相对行列索引与精确坐标矩形）

#### `BlobAnalysis` - 连通域与斑点分析
用于产品缺陷检测、焊点统计或颗粒计数。
- **输入参数：**
  - `connectivity`: 邻域模型（`4` 或 `8` 连通）。
  - `min_area` / `max_area`: 斑点面积上下限过滤。
- **输出类型：** `Point`（目标质心点及各区域统计元数据）

#### `ShapeRecognition` - 几何形状识别与匹配
- **输入参数：**
  - `mode`: `GeometricClassify`（根据多边形拟合度自动分类）或 `TemplateMatch`（特定形状特征比对）。
  - `target_shape`: `Circle`, `Rectangle`, `Triangle`, `Polygon`。
- **输出类型：** `string`（形状类别名称与置信度）

#### `ImageComparison` - 图像比对与变动分析
- **输入参数：**
  - `image_a` / `image_b`: 两张比对图。
  - `diff_threshold`: 像素色差敏感度阈值。
  - `diff_output_path`: 变动区域红色外接框标注图保存路径。
- **输出类型：** `real`（相似度分数，0.0~1.0）

---

### 4. 几何变换与色彩空间 (Geometric Transform & Color Space)

- **`CropImage`**：支持 `Rect`（自由矩形）与 `Center`（中心锚点扩充裁剪），内置画布越界钳位保护。
- **`ResizeImage`**：支持 `Dimensions`（指定绝对宽高）与 `Scale`（指定缩放比），可选 `keep_aspect_ratio` 锁定纵横比。
- **`ImageRotate`**：支持 `90`、`180`、`270` 度旋转，与 `Horizontal` / `Vertical` 水平/垂直镜像翻转。
- **`CvtColor`**：支持 `RGB2GRAY`、`BGR2GRAY`、`RGB2HSV`、`BGR2RGB` 色彩空间变换。

---

## 📦 插件清单定义 (Manifest Reference)

```json
{
  "plugin_id": "xy_image",
  "name": "官方计算机视觉与图像处理套件 (Computer Vision & Image Suite)",
  "version": "0.50.5",
  "group": "Image",
  "group_icon": "🖼",
  "description": "工业级自研视觉引擎，提供高精度NCC模板匹配、多点找色、像素拾色、表格网格识别、智能二值化、形态学与轮廓形状分析能力",
  "actions": [...]
}
```

---

## 📄 许可证 (License)

本插件遵循免费专有许可协议 (Freeware)。供 小友+ 用户免费下载与使用，未经官方书面授权，严禁对二进制文件进行逆向工程、反编译或二次打包转售。
