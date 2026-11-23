# 仓库穿梭无人车（AGV）智能调度技术报告（LaTeX 源码仓库）

本仓库存放《人工智能基础》大作业最终技术报告的 LaTeX（`.tex`）源码，配套实验代码与复现仓库位于：
[agv-warehouse-scheduling-2026](https://github.com/Fallen-Crystal/agv-warehouse-scheduling-2026)。

---

## 1. 排版规范与版式说明（参考 NeurIPS 学术论文版式）

- **字号与行距**：正文采用标准学术论文 `10pt`（五号 `zihao=5`）与紧凑行距（`\linespread{1.18}`）；标题采用上下双横线（上粗下细）配 `15.5pt` 居中黑体加粗；作者学号与姓名采用 `10pt` 加粗居中；摘要标题居中（`11.5pt` 加粗）；一级/二级/三级标题分别为 `12pt` / `10.5pt` / `10pt` 纯黑加粗。
- **色彩规范**：所有标题、正文字体、图表题注与公式全部使用**纯黑色**；插图（TikZ 架构图、演化图与实验数据图）采用彩色渲染以增强可读性。
- **页眉与页脚**：
  - **第 1 页**：顶部居中显示 `《人工智能基础》大作业` 及单横线（P2 样式），标题下方居中列出 2 位组员的学号与姓名（P3 样式）。
  - **第 2 页起**：不显示任何页眉与页眉横线（移除 P4 样式），仅保留底部居中页码。

---

## 2. 按 Git 提交历史的章节完成状态与队友留白索引

根据主代码仓库 `agv-warehouse-scheduling-2026` 的 Git 提交记录，**`Fallen-Crystal`（含 `Fallen` / `落叶` / `Codex`）负责推送的所有模块、算法与实验章节已全部撰写完毕（含完整公式、数据总表与 `figures/` 下的 15 张高清实验图表）**；队友 **`Betty-dey`（`xiejy0920@163.com`）** 负责推送的部分已使用 `\begin{teammatebox}{...}` 精准留白，方便队友直接填入：

| 章节文件 | 小节编号与标题 | 当前状态 | 对应代码仓库 Git 提交归属 |
|---|---|---|---|
| `sections/00_abstract.tex` | 摘要与关键词 | **已完成** | 全文汇总（定稿后可微调） |
| `sections/01_introduction.tex` | 1. 引言与问题背景（1.1–1.4） | **已完成** | 课题背景、四大技术难点、主要贡献与结构 |
| `sections/02_methodology_overview.tex` | 2. 解决方法概要（2.1–2.3） | **已完成** | 三层协同架构（图 1）、双主线定位（表 1）与评价口径 |
| `sections/03_evolution.tex` | 3. 思路推进与方案演化（3.1–3.4） | **已完成** | 双主线演化脉络（图 2）、探索分支复盘与对照总表（表 2） |
| `sections/04_modeling.tex` | **4.1** 离散网格拓扑与分层/混合货架几何建模（Legacy / V4 / V9） | **已完成** | `Fallen-Crystal` (`fbc62ca..d6b713e`) |
| `sections/04_modeling.tex` | **4.2** 离散时空无碰撞约束、因果观测边界与通用评价指标 | **已完成** | `Fallen-Crystal` (`29d86e7`, `8551943`, `ea719b5`) |
| `sections/04_modeling.tex` | **4.3** V9.1 开放流关闭契约、空闲待命策略建模与验解边界 | **留白待队友填写** | `Betty-dey` (`ceed0db`, `a9c469a..81dc593`) |
| `sections/04_modeling.tex` | **4.4** WEPAStacks 真实工业订单流映射模型与固定尺度线性目标 | **留白待队友填写** | `Betty-dey` (`ef73cd5`) |
| `sections/05_algorithms.tex` | **5.1** 基于增量时空预约表的 SIPP 路径规划与几何加速 | **已完成** | `Fallen-Crystal` (`29d86e7`, `6d21289`, `ea719b5`) |
| `sections/05_algorithms.tex` | **5.2** 拥堵关联 LNS 修复、静态批滚动与 BCRD 影子试派（含 V9.1 选点与 P90 保护） | **已完成** | `Fallen-Crystal` (`d79aa07`, `90b98ef..e135284`, `73c56b9..bd5f26b`) |
| `sections/05_algorithms.tex` | **5.3** 面向 WEPA 真实订单流的事件门控软分区联合遗传算法（`gate`） | **留白待队友填写** | `Betty-dey` (`ef73cd5`, `d1d36f1`) |
| `sections/05_algorithms.tex` | **5.4** 双概率自适应遗传算子与 Double DQN 元调度探索 | **已完成** | `Fallen-Crystal` / `Codex` (`f329d78`, `ea719b5`, `fe8d009`) |
| `sections/05_algorithms.tex` | **5.5** 零依赖工程架构、服务边界解耦与本地 Web 可视化系统 | **已完成** | `Fallen-Crystal` (`9a73bf4..5c346b6`) |
| `sections/06_experiments.tex` | **6.1** 实验体系总览与独立物理验解协议 | **已完成** | `Fallen-Crystal` (`fe8d009`, `2e89978`, `ac8afe9`) |
| `sections/06_experiments.tex` | **6.2** 主线 B 早期阶段诊断与微型 CP-SAT 精确参照对比实验 | **留白待队友填写** | `Betty-dey` (`ef73cd5`, `ed2bd0a`) |
| `sections/06_experiments.tex` | **6.3** 主线 B 多随机种子稳定性、超参敏感性与跨窗口泛化复评（356 次运行 + DQN） | **已完成** | `Fallen-Crystal` (`fe8d009`, `2e89978`, `ea719b5`) |
| `sections/06_experiments.tex` | **6.4.1–6.4.3** 主线 A 多工况 5-Seed 演进、V4 BCRD 留出（1,400 次）与 V9.1 留出（960 次） | **已完成** | `Fallen-Crystal` (`90b98ef..e135284`, `73c56b9..bd5f26b`, `2e89978`) |
| `sections/06_experiments.tex` | **6.4.4** V9.1 空闲待命策略专项对比实验（`idle-policy-20261016`） | **留白待队友填写** | `Betty-dey` (`ceed0db`) |
| `sections/07_conclusion.tex` | **7.1–7.2** 全文工作总结与未来展望（附队友补充留白框） | **已完成** | 双人汇总（队友可补充后移除提示框） |

---

## 3. 填写学号姓名与编译说明

1. 打开 `main.tex`，修改顶部 4 行宏定义填写 2 位组员的学号与姓名：
   ```latex
   \newcommand{\StudentOneID}{待填写学号1}
   \newcommand{\StudentOneName}{待填写姓名1}
   \newcommand{\StudentTwoID}{待填写学号2}
   \newcommand{\StudentTwoName}{待填写姓名2}
   ```
2. **编译方式**：
   - **Overleaf**：导入本仓库，左上角 `Menu -> Compiler` 选择 **`XeLaTeX`** 编译。
   - **本地 Tectonic**：执行 `tectonic -X compile main.tex`。
   - **本地 TeX Live / MiKTeX**：依次执行 `xelatex main.tex` -> `bibtex main` -> `xelatex main.tex` -> `xelatex main.tex`。
