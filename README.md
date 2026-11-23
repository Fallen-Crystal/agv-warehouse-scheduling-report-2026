# 仓库穿梭无人车（AGV）智能调度技术报告（LaTeX 源码仓库）

本仓库存放《人工智能基础》大作业最终技术报告的 LaTeX（`.tex`）源码，配套实验代码与复现仓库位于：
[agv-warehouse-scheduling-2026](https://github.com/Fallen-Crystal/agv-warehouse-scheduling-2026)。

---

## 1. 报告总体风格与格式约定

- **行文风格**：采用学术论文结构与客观严谨的工程语言（避免口语化与大段粘贴源码），以“问题驱动—方法设计—演进对比—实验验证”为主线展开。
- **页面格式**：
  - **首页页眉**：仅在第一页顶部居中显示 `《人工智能基础》大作业` 及单横线。
  - **作者署名**：标题下方、正文之前居中列出 2 位组员的学号与姓名（在 `main.tex` 顶部宏定义处统一修改）。
  - **后续页眉**：第 2 页起不显示任何页眉与页眉横线，仅保留底部居中页码。

---

## 2. 撰写思路与章节规划（当前进度）

报告按标准学术论文划分为 7 个主体章节，**已按章节拆分为独立 `.tex` 文件以便双人并行协作、减少 Git 合并冲突**：

| 文件 | 章节标题 | 当前状态 | 内容定位与分工建议 |
|---|---|---|---|
| `main.tex` / `preamble.tex` | 主控文件与排版样式 | **已完成** | 跨平台中文字体自适应、首页页眉与无后续页眉、标题与双人署名区 |
| `sections/00_abstract.tex` | 摘要与关键词 | **初稿已完成** | 凝练问题、方法与核心量化结论（全文定稿后同步微调） |
| `sections/01_introduction.tex` | 1. 引言与问题背景 | **初稿已完成** | 自动化立体仓库背景、多 AGV 并发调度核心难点、研究目标与主要贡献 |
| `sections/02_methodology_overview.tex` | 2. 解决方法概要 | **初稿已完成** | 三层协同架构（TikZ 图）、双主线分工、最终采用的 `gate` 与 `src/agv/` 方案概览 |
| `sections/03_evolution.tex` | 3. 思路推进与方案演化 | **初稿已完成** | 主线 A 与主线 B 的问题驱动演进脉络、TikZ 演进图、探索性分支复盘与对照总表 |
| `sections/04_modeling.tex` | 4. 问题形式化建模与物理约束 | **框架已搭，待合写** | 栅格与多层货架图模型、时空无碰撞约束、层序/装卸/待命/返库规则与目标函数公式 |
| `sections/05_algorithms.tex` | 5. 核心调度与路径规划算法设计 | **框架已搭，待合写** | SIPP 安全区间规划、软分区联合 GA 与事件门控机制（伪代码）、BCRD 影子试派与 LNS 修复 |
| `sections/06_experiments.tex` | 6. 实验设计与结果分析 | **框架已搭，待合写** | 主线 B（WEPA 开发/验证窗 + 预算/自适应/多 seed）与主线 A（5-seed 演进与超参扫描）图表分析 |
| `sections/07_conclusion.tex` | 7. 总结与展望 | **框架已搭，待合写** | 核心成果总结、工程复现说明、局限性分析与后续研究方向 |
| `references.bib` | 参考文献库 | **基础条目已就绪** | 已录入 SIPP、Lifelong MAPF、MAPF-LNS、Hungarian、ALNS、HGS、SLAPStack 等核心文献 |

---

## 3. 填写作者信息与编译方式

### 3.1 填写组员学号与姓名

打开 `main.tex`，修改顶部 4 行宏定义即可自动更新首页居中署名：

```latex
\newcommand{\StudentOneID}{XXXXXXXXXXXX}
\newcommand{\StudentOneName}{成员一}
\newcommand{\StudentTwoID}{XXXXXXXXXXXX}
\newcommand{\StudentTwoName}{成员二}
```

### 3.2 本地编译与 Overleaf 协作

本模板通过 `preamble.tex` 内置跨平台字体回退（自动兼容 Windows 宋体/黑体、macOS Songti SC/Heiti SC 与 Linux/Overleaf Fandol 字体），推荐使用以下任意方式编译：

- **方式 A：Overleaf 在线协作（推荐）**
  - 在 Overleaf 中导入本 GitHub 仓库（或上传压缩包），在左上角 `Menu -> Compiler` 选择 **`XeLaTeX`**，点击 `Recompile` 即可。
- **方式 B：macOS / Linux 本地 Tectonic（一键编译含参考文献）**
  ```bash
  tectonic main.tex
  ```
- **方式 C：TeX Live / MiKTeX 本地 XeLaTeX**
  ```bash
  xelatex main.tex
  bibtex main
  xelatex main.tex
  xelatex main.tex
  ```

---

## 4. 协作流程建议

1. 两人商定第 4–7 章的具体分工后，各自在独立分支（如 `feat/sec4-modeling`、`feat/sec6-experiments`）编辑对应的 `sections/0x_*.tex`。
2. 实验配图统一放入 `figures/` 目录，推荐使用高分辨率 PNG（≥300 DPI）或矢量 PDF，文件名采用英文小写加连字符（如 `wepa-val-comparison.png`）。
3. 仓库已通过 `.gitignore` 忽略编译生成的临时文件与 `main.pdf`，提交时仅保留 `.tex`、`.bib` 与 `figures/` 素材，避免二进制冲突。
