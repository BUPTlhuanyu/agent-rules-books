# 代码质量类规则概要

本文只覆盖仓库中与「代码质量」直接相关的 6 套规则（其余为架构、DDD、数据与可靠性类）：
`clean-code`、`code-complete`、`a-philosophy-of-software-design`、`refactoring`、`refactoring-guru`、`the-pragmatic-programmer`，并把 `working-effectively-with-legacy-code` 作为「无测试保护时的前置条件」一并说明。

## 1. 规则的组织方式

每本书发布三个版本（数据取自 [README.md](../README.md) 的 Release Matrix，规则数按 Markdown 列表项统计）：

- `full`：唯一权威源，位于 `<book>/<book>.md`，按主题分节的长清单（Clean Code 220 条 / Refactoring.Guru 478 条）
- `mini`：日常使用与做成 skill 的推荐版本（29–47 条）
- `nano`：常驻上下文极紧时的兜底版本（14–26 条）

`mini` / `nano` 由 `_rule-workbench/` 生成，每本书都有 `traceability.md`，把每条压缩规则映射回 `full.md` 的章节与行号（例如 `_rule-workbench/clean-code/traceability.md:18` 的 `M1` 溯源到 `Priority and behavior` (5-12) 等 5 个章节），并显式记录被合并或「intentionally lost」的内容。压缩目标是 **decision-equivalent 而非 sentence-equivalent**（`_rule-workbench/PROCESS.md:5`）。

`mini` / `nano` 统一为 5 段结构：When to use / Primary bias to correct / Decision rules / Trigger rules / Final checklist。这个形状对 agent 很友好：先给适用场景，再给一句「要纠正的偏差」，再是常规决策、触发式规则和收尾自查。

## 2. 各套规则的定位与核心偏差

- **Clean Code**（full 220 / mini 29 / nano 14）：微观可读性层。要纠正的偏差是「能跑的代码不等于干净的代码」。重点在命名、小函数、单一抽象层级、命令与查询分离、参数设计、注释纪律、happy path 可读、测试即生产代码。
- **Code Complete**（180 / 38 / 23）：构造纪律层，偏「缺陷预防」。强调先确认需求/架构/约定是否清楚、伪代码先行、数据类型让非法值难以表达、控制流可检查、信任边界校验、断言 vs 领域错误的区分、基于证据的性能调优。
- **A Philosophy of Software Design**（177 / 28 / 17）：复杂度层。唯一成功指标是认知负担下降；主张 deep module、信息隐藏、把复杂度向下压、拒绝薄封装与 pass-through 层。它与 Clean Code 在「小即是好」上存在张力，兼容矩阵把两者标为 🔁 overlap。
- **Refactoring**（242 / 31 / 19）：行为保持的小步改造。核心是 preparatory / follow-up refactoring、结构改动与行为改动分离、先有安全网、按「当前阻塞的 smell」而非所有 smell 动手、有明确停止条件。
- **Refactoring.Guru**（478 / 46 / 23）：Refactoring 的「诊断—处置」加强版，规则数最多。先诊断 smell（症状、成本、范围、验证路径、停止条件），再选最小手法；按 bloaters / OO abusers / change preventers / dispensables / couplers 分类扫描；含 Rule of Three、公共 API 兼容性、抽取前的输入输出与不变量检查。与 Refactoring 为 🔁 overlap，二选一。
- **The Pragmatic Programmer**（179 / 47 / 26）：工程操作风格层。知识级 DRY（每个事实一个权威归属）、正交性、可逆决策、tracer bullet、契约与资源所有权显式化、重复劳动自动化、破窗理论。与 Clean Code / Code Complete 均为 🔁 overlap。
- **Working Effectively with Legacy Code**（193 / 32 / 17）：不是质量目标本身，而是前置条件。无可信测试的区域先「取得控制」——characterization test、seam、断依赖，再谈改造；明确禁止以重写代替接缝。

## 3. 六套规则共享的骨架

不同书的措辞不同，但落到 agent 决策上反复出现同一组要求：

- 行为改动、结构改动、测试更新三者分离，patch 保持可评审
- 每个事实/知识只有一个归属地；重复到第三次必须消除（Rule of Three）
- 函数不要混合 setup / 校验 / 计算 / 副作用；查询不要顺带改状态
- 布尔开关参数、暴露的内部表示、train-wreck 调用链一律视为设计缺口
- 注释只写 rationale、契约、约束；解释控制流的注释先改代码
- 框架、持久化、厂商、构造细节留在边界之外
- 抽象必须由当前证据支撑，禁止投机式封装；清理要有停止条件
- 收尾前必须真正跑过相关测试或检查

## 4. 怎么选（组合建议）

按 [USAGE.md](USAGE.md) 与 [COMPATIBILITY.md](COMPATIBILITY.md)，质量类规则的推荐用法是「一层常驻 + 一层按需」：

- 日常实现与评审：`clean-code.mini`（或想要更强的缺陷预防纪律时换 `code-complete.mini`，二者 🔁 overlap，不要同时常驻）
- 模块与 API 设计、觉得改动别扭时：`a-philosophy-of-software-design.mini`（与 `clean-code` 🔁，宜按任务切换而非叠加）
- 重构专项：`refactoring.mini` 或 `refactoring-guru.mini` 二选一，做成按需触发的 skill
- 缺测试的老代码：先挂 `working-effectively-with-legacy-code.mini`，取得控制后再叠重构规则
- 团队工程习惯基线：`the-pragmatic-programmer.mini`，但它与 `clean-code` / `code-complete` 🔁

`full` 只用于审计、派生小规则或深度会话的参考文件；`nano` 只在常驻预算极小或需跨编辑器移植时使用。

## 5. 质量与已知短板

优点：溯源完整（每条 mini/nano 规则可回到 full 的章节行号）、压缩过程本身有成文标准与验证清单、保留了各书自身的偏差而没有被抹平成通用风格指南、14×14 兼容矩阵显式标出 2 处冲突与 11 处重叠。

短板（[CRITICISM.md](CRITICISM.md) 已自评）：

- 缺少真实效果度量。唯一实验是 `vibe-coded-crap` 项目上 APoSD mini rules 与「只提书名」的对比，由 ChatGPT 打分 74 vs 46；同时 Reek smell 数几乎没差（1083 vs 1077）。属早期定性信号，不是 benchmark。
- 规则总量大，全量加载会挤占任务上下文；缓解手段是 mini/nano 分层与按需加载，但无法强制。
- 规则来自书本而非真实事故，缺少 incident-derived 规则的采集机制。
- 存在「表面合规」风险：agent 可能产出看起来讲原则、却没解决实际约束的代码，目前没有 outcome eval 能证伪。
- 冲突治理靠加载纪律与兼容矩阵的定性判断，没有形式化的冲突消解规则。
