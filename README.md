# John Tromp's Lambda Diagrams - Minimalist Dynamic Workstation

An interactive educational workstation for visualizing and evaluating **John Tromp's Lambda Diagrams** using a pure black-and-white minimalist design, complete with dual-language support (Chinese / English) and physical line-morphing animation.

## 核心设计与视觉体系 (Core Design)

- **纯黑白极简主义 (Monochrome Minimalism)**: 彻底去除 Emoji，采用高对比度无彩色黑白线条、纯净版面与精准字偶距排版，呈现纯粹的几何导线与电路拓扑美感。
- **中英文多语言切换 (Bilingual Support)**: 界面右上角提供专门语言切换按钮（`[ English / 浅色模式 / 图解指南 / 关于 Tromp ]`），所有界面文本、操作提示、预置库说明、图解指南及五阶段归约解说均支持中英文即时无缝切换。
- **浅色 / 深色模式切换**: 提供纯黑（Dark Obsidian）与极简浅色（Light Paper）双主题模式。
- **严格符合 John Tromp 原生几何规范**: 经比对 John Tromp 原始位图矩阵，抽象条为水平横梁（带 Serif 悬挑），变量为连续垂直导线从其所属绑定横梁起始向下延伸并接驳于应用横梁，应用桥水平接驳函数与实参。
- **默认启用纯净视口**: 显示标签与平滑动画默认全部自动开启，移除顶部工具栏冗余复选框按钮，工具栏仅保留视图切换、渲染风格与矢量/位图导出。

---

## 核心功能 (Features)

1. **多格式输入与解析**:
   - **经典记法 (Named / Classic)**: 支持 `λx. x`、`\x. x`、`/x. x`，多参数简写（`\x y z. expr`），括号左结合应用及 `let x = e in b` 语法糖。
   - **德布鲁因记法 (De Bruijn Notation)**: 原生支持直接输入无变量名索引序列（如 `λλ1`、`\ \ 2 (2 1)`、`/ / 1`）。
   - **自由变量智能支持**: 自动识别并优雅处理开放项。

2. **双风格图样渲染 (Dual-Style Rendering)**:
   - **标准风格 (Standard Style)**: 应用连接线连向函数的*最左侧变量*（Leftmost Variable），规范、严谨。
   - **替代风格 (Alternative Style)**: 应用连接线连向*最近的深层变量*（Nearest Deepest Variable），线条紧凑、富有机理感。

3. **极简预设公式库弹窗列表 (Preset Formulas Modal Table)**:
   - 彻底摒弃传统原生下拉菜单，改为弹出式极简全览选择列表表格。
   - 包含 23 个涵盖 Church 计数、核心组合子 (I, K, S, B, C, W, SKK, Y, Ω)、布尔与算术运算 (SUCC, ADD, MULT, PRED, AND, OR, NOT) 以及 Tromp 167 位素数筛片段的经典项。
   - 提供即时搜索框与类别过滤标签（全部 / Church / 基础组合子 / 算术与逻辑 / Tromp 经典项）。
   - 点击表格任意行或 [载入] 按钮即刻加载并解析渲染。

4. **无上下箭头的长圆柱极简滚动条 (Strictly Button-Free Cylinder Scrollbar)**:
   - 彻底排查并移除了触发 Chromium / Windows 原生上下箭头的标准 `scrollbar-width` 声明。
   - 全局界面、历史表格与弹窗采用纯粹的 6px 宽长圆柱体滑块（`border-radius: 9999px`）。
   - 严格覆盖禁用所有 `::-webkit-scrollbar-button` 伪类分支，杜绝任何递增/递减箭头按钮。

5. **空间紧凑型规约历史表格 (Compact Step History Table)**:
   - 摒弃以往臃肿且重复提示“第几步”的纵向卡片列表，改为高信息密度紧凑型数据表格。
   - 表头包含序号 `#`、`规则 (Rule)`、`表达式 (Term)`。
   - 消除重复字样，每一行直观呈现该步所得的数学项，点击任意行立即瞬时跳转回溯，当前激活步带有醒目左侧强调线。

6. **高感知度五阶段 β-归约视觉系统 (Visceral 5-Phase β-Reduction Visuals)**:
   - **阶段 1 (锁定红基 / Redex)**: 待求值红基 `((λx. M) N)` 触发焦点框高亮与脉冲应用桥，非红基外部节点自动淡化降噪，桥上方浮动显著的 `REDEX` 标识。
   - **阶段 2 (关联形参与实参 / Vars & Arg)**: 实参子图 $N$ 被清晰虚线容器框选并标明实参项，形参垂线端点亮起指示信标，动态绘制连接实参到形参端口的弧形代换流向线。
   - **阶段 3 (溶解横梁与开启插槽 / Dissolve λ & Sockets)**: $\lambda x$ 抽象横梁与红基连接桥同步溶解虚化并打上溶解标签，形参垂线末端开启醒目的双同心环参数接收插槽（`◎`）。
   - **阶段 4 (执行代换接入 / Substitute)**: 在各形参插槽直接接入实参迷你接驳块 `[代入实参: N]`；若形参引用为 0（如 K 组合子），则在实参上呈现大号删除线及丢弃提示。
   - **阶段 5 (最终项整流归位 / Settle)**: 项以标准规范 Tromp 几何网格稳态归位，顶部标注结算成功标识。

7. **加粗几何导线 (Reinforced Circuit Line Weights)**:
   - 抽象横梁线宽由 3px 全面加粗至 **5px**；变量垂直引线与应用连接桥由 2.5px 加粗至 **4px**；红基脉冲桥加粗至 **6px**；接驳圆点半径扩大至 **4.5px**。大幅强化工程图纸式的视觉厚度与高分辨下的清晰辨识度。

8. **彻底消除自动播放频闪 (Flicker-Free Continuous Auto-Play Pipeline)**:
   - **平滑视觉流**: 自动播放时自动抑制 Phase 1 局部淡化 (`diag-dimmed`) 与瞬态高亮框，保持全图恒定高对比度与纯净背景，杜绝每步之间的黑白明暗闪烁。
   - **严格时序防竞态**: 废除旧有的定时器与补间动画并发竞态，改为每一阶动画平滑抵达规范坐标并结算后，才进入舒适视距停留期并触发下一阶，彻底消除掉帧与重绘频闪。

9. **动态生长与动态收缩动画 (Axis-Aligned Dynamic Growth & Retraction)**:
   - **新生线段动态生长**: 新出现的抽象横梁自中点向两侧对称延伸扩展；新变量垂线自绑定横梁向下如垂直导线般动态生长垂落；应用横梁自函数引线向右搭桥延展，拒绝任何突兀跳出。
   - **消解线段动态回缩**: 溶解的抽象横梁向中点动态收缩至零；待求值应用桥向原点收拢回撤；被替换变量垂线平滑内缩融入插槽；K 组合子等被丢弃的子树沿几何中心整体内聚塌缩并虚化，告别生硬突消。
   - **标签与焊点同步插值**: 符号标签与接驳圆点全程紧贴关联导线实时联动插值，彻底消除文本断续闪灭。

10. **极简一排七键纯 SVG 规约控制栏 (Single-Row 7-Button SVG Control Bar)**:
    - 彻底移除了原先分散且占空间的文字按钮组，重构成**单排 7 列纯 SVG 矢量图标控制栏**，零文字遮挡、零冗余：
      1. `|<` **重置 (Reset)** (`#macroResetBtn` / `R`)：瞬时回退至初始状态（第 0 步）。
      2. `<<` **宏步后退 (Macro Step Back)** (`#macroPrevBtn` / `←`)：回退至上一个宏规约项。
      3. `<` **微步后退 (Micro Phase Back)** (`#microPrevBtn`)：回退至上一个演算微阶段。
      4. `Play / Pause` **自动演示 / 暂停 (Play / Pause)** (`#playPauseBtn` / `Space`)：居中主控高亮按钮，播放与暂停图标智能切换。
      5. `>` **微步前进 (Micro Phase Forward)** (`#microNextBtn` / `Shift+→`)：单步步进至下一演算微阶段。
      6. `>>` **单步规约 (Macro Step Forward)** (`#macroNextBtn` / `→`)：直接执行一次完整 β-规约。
      7. `>|` **规约至范式 (Reduce to Normal Form)** (`#reduceNormalFormBtn`)：一键全速快进至最终无红基范式。
    - 所有按钮配备无障碍 `title` / `aria-label` 悬浮提示，并在中英文切换时即时同步更新。

11. **图形交互与操作**:
    - 鼠标左键按住拖拽即可全局平移；滚轮以鼠标光标为锚点平滑缩放。
    - 支持直接点击画布上的发光应用桥进行定向规约。
    - 快捷键支持: `Space` 播放/暂停，`→` 宏单步，`Shift+→` 微分步，`←` 回退，`R` 重置，`F` 视口适配，`Esc` 关闭弹窗。

12. **导出功能**:
    - 一键导出高精度矢量 SVG。
    - 一键导出 2x Retina 高清抗锯齿 PNG。
    - 一键复制 Unicode 制表字符画 (`boxChar`) 与 Raw ASCII 网格。

---

## 本地启动与使用

直接双击或使用任意现代浏览器打开 `index.html` 即可运行：

```bash
# Windows
start lambdaDiagram/index.html
```
