# 🌟 从虚拟里拿出一颗真心 · 星瞳五周年演唱会RE弹幕可视化

<p align="center">
  <img src="https://img.shields.io/badge/数据量-56%2C402条弹幕-4A9EFF?style=for-the-badge" alt="数据量">
  <img src="https://img.shields.io/badge/时长-186.7分钟-FFD1EC?style=for-the-badge" alt="时长">
  <img src="https://img.shields.io/badge/技术栈-ECharts%205-52C41A?style=for-the-badge" alt="技术栈">
  <img src="https://img.shields.io/badge/版本-v12%20稳定版-2E8B57?style=for-the-badge" alt="版本">
</p>

> **主题**：「从虚拟里拿出一颗真心」  
> 星瞳五周年演唱会RE直播弹幕数据全景可视化，56,402 条真实弹幕的情感图谱。  
> 她从虚拟世界走来，拿出的却是最真实的心。小星星们亦然。

---

## 🚀 快速开始

```bash
# 直接双击打开（纯静态，无需服务器）
dist/index.html      # 主可视化页面
dist/analyzer.html   # 弹幕分析器（上传自定义弹幕文件）

# 或使用本地服务器获得完整体验
cd dist && python -m http.server 8080
# → http://localhost:8080
```

> ⚠️ 词云图表依赖 ECharts CDN，需要网络连接。分析器支持纯前端处理，无需后端。

---

## ✨ 功能特性

### 可视化图表（13 个）

| # | 图表 | 说明 |
|---|------|------|
| 1 | 🌠 弹幕雨动效 | 真实弹幕滚动，7 轨道防重叠 + 淡入淡出 |
| 2 | 📜 高频词滚动条 | 关键词无缝横向滚动，悬停暂停 |
| 3 | 📈 弹幕时间轴 | 187 分钟折线图，6 峰值事件标注，支持时段筛选 |
| 4 | ⚡ 速率热力轨道 | 10 秒粒度密度图，颜色深浅映射密集程度 |
| 5 | ☁️ 弹幕词云 | 50 高频词圆布局，蓝白渐变，词云→弹幕联动抽屉 |
| 6 | 💫 情感分布环形图 | 11 类情感细分，「其他」仅占 32% |
| 7 | 🎭 情感标签卡片 | 每类情感的数量 / 占比详情 |
| 8 | 📊 情感量化对比 | 各情感绝对数量横向柱状图 |
| 9 | 🌡️ 时空热力矩阵 | 时间×情感交叉热力图 |
| 10 | 🏆 Top 弹幕排行 | 柱状图 + 列表双视图 |
| 11 | 🔵 速度仪表盘 | 峰值 + 平均速率双层仪表 |
| 12 | 🕸️ 文化雷达图 | 五维特征：互动 / 情感强度 / 梗文化 / 应援密度 / 节奏感 |
| 13 | 🌊 情感时间流 | 堆积面积图展示情感时序变化 |

### 特色组件

| 组件 | 说明 |
|------|------|
| 🖼️ 弹幕照片墙 | CSS Grid 全屏网格，56502 条弹幕按情感着色平铺，hover 放大 |
| 💬 名句彩蛋 | 12 张精选弹幕卡片，支持按情感分类筛选 |
| 🔍 词云联动抽屉 | 点击词云词语 → 右侧滑入相关弹幕（时间戳 + 情感标签 + 关键词高亮），毫秒级索引查询 |
| 📸 分享海报生成器 | Canvas 渲染精美数据海报，一键下载 PNG |
| 🔬 弹幕分析器 | 独立页面 `analyzer.html`，纯前端展示 11 类分析图表，支持导出 Markdown 报告 |

### 视觉特效

- ✨ Canvas 星星粒子背景（含流星划过）
- 🌟 英雄区浮动粒子动效
- 🪟 毛玻璃卡片（backdrop-filter）
- 📡 Intersection Observer 滚动进场动画
- 🔢 数字跳动计数动效
- 🎨 星瞳品牌色系（`#0A1230` 深夜星空 + `#4A9EFF` 星光蓝 + `#FFD1EC` 粉白）

---

## 📊 数据亮点

| 指标 | 数值 |
|------|------|
| 总弹幕数 | **56,402 条** |
| 直播时长 | **186.7 分钟** |
| 峰值时刻 | **第 43 分钟，657 条 / 分钟** |
| 平均速率 | **302 条 / 分钟** |
| 全场最热弹幕 | **mua（2,521 次）** |
| 情感 TOP1 | **应援，占 23.4%** |

---

## 📦 项目结构

```
danmu-viz/
├── index.html              # 主可视化页面（内嵌全量数据）
├── analyzer.html           # 弹幕分析器（上传 txt，纯前端分析）
├── README.md               # 本文档
├── scripts/
│   ├── process_data.py     # 情感分类 + 统计 + 词频 + 时序 JSON 生成
│   └── gen_danmu_wall.py   # 照片墙 + 词云索引 JSON 生成
├── data/                   # 处理后 JSON（11 个文件）
│   ├── stats.json
│   ├── danmu_timeline.json
│   ├── wordcloud_data.json
│   ├── emotion_data.json
│   ├── emotion_timeline.json
│   ├── top_messages.json
│   ├── heatmap_data.json
│   ├── radar_data.json
│   ├── sample_danmus.json
│   ├── danmu_wall.json
│   └── danmu_index.json
└── dist/                   # ⭐ GitHub Pages 部署包（含 .nojekyll）
    ├── index.html
    ├── analyzer.html
    ├── README.md
    └── data/               # JSON 数据副本
```

---

## 🌐 部署到 GitHub Pages

1. 新建 GitHub **公开仓库**
2. 将 `dist/` 目录下所有文件上传至仓库根目录
3. 仓库 Settings → Pages → Source：`main` 分支 `/ (root)` → Save
4. 1-2 分钟后访问 `https://你的用户名.github.io/仓库名`

> `dist/` 下已包含 `.nojekyll`，确保 Jekyll 不会误处理 `data/` 下的 JSON 文件。

---

## 🛠️ 技术栈

| 技术 | 用途 |
|------|------|
| HTML5 + CSS3 | 布局、渐变、毛玻璃、动画 |
| Vanilla JavaScript | 图表控制、互动逻辑、动效 |
| ECharts 5.4 | 折线图 / 饼图 / 柱状图 / 热力图 / 仪表盘 / 雷达图 |
| ECharts WordCloud | 词云扩展 |
| Canvas API | 粒子背景、流星、海报导出 |
| IntersectionObserver | 懒加载 + 滚动进场 |
| CSS Grid + Flexbox | 照片墙自适应布局 |

**零构建工具、零框架**，纯静态 HTML 文件直接打开即用。

---

## 📝 数据说明

- **来源**：星瞳五周年演唱会RE直播弹幕（2025 年）
- **格式**：`timestamp:content`（13 位毫秒 Unix 时间戳）
- **处理**：Python 脚本进行时序聚合、词频统计、情感分类
- **情感分类**：11 类细分（爱意 / 欢呼 / 欢笑 / 应援 / 感慨 / 调侃 / 互动 / 疑问 / 玩梗 / 赞美 / 陪伴），基于关键词词典 + 模式回退优先级匹配

---

## 🔄 更新日志

### v12（2026-06-09）— 分析器稳定性修复，当前稳定版

- 🐛 修复雷达图 5 处情感名与分类引擎不一致导致渲染静默失败
- 🐛 修复 `Math.max(...arr)` 大数组展开栈溢出（`maxOfArray()` 循环替代）
- 🐛 `processFile` / `renderAll` 的 `setTimeout` 回调包裹 try-catch，异常弹窗提示
- ✅ 全链路 p1.txt 56285 条弹幕渲染验证通过

### v11（2026-06-09）— 照片墙排版优化

- 🎨 `.wall-grid` 新增 `align-items: start` 防止 CSS Grid 强制等高截断文字
- 🎨 限制 `-webkit-line-clamp: 2`，每卡最多 2 行
- 🎨 `padding` 收紧、`line-height` 压缩，文字向上靠拢

### v10（2026-06-09）— 分析器大文件解析修复

- 🐛 `Math.min/max(...timestamps)` 对 5.6 万元素展开栈溢出 → 循环替代
- 🐛 空内容行（`timestamp:`）误解析修复

### v9（2026-06-09）— 情感分类全面升级

- 🎯 5 类 → 11 类，关键词词典扩大 5 倍 + 模式回退匹配
- 📉 「其他」占比从 64% 降至 32%
- 🔀 `process_data.py` 与 `gen_danmu_wall.py` 统一关键词词典

### v8（2026-06-09）— Bug 修复版

- 🐛 时间轴峰值标注对齐 · 照片墙重试机制 · 词云索引 O(1) 查询
- 🐛 分析器散点图 / 时段摘要 / 弹幕格式全面修复

### v7（2026-06-08）— 交互增强版

- 🆕 词云联动抽屉 · 弹幕照片墙 · TF-IDF 智能时段摘要 · 长度直方图 + 浓度散点图

---

<p align="center">
  小星星们，谢谢你们的每一条弹幕 💙<br>
  虚拟里拿出的，是最真实的一颗心。
</p>
