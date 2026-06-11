---
name: product-lifecycle
description: 产品全链路工作流技能——覆盖"想法孵化→需求判别→方案设计→竞品分析→商业模式→战略规划→架构设计→功能设计→指标ROI→产物输出→项目管理"完整流程，并在关键节点引入7个虚拟角色审核，产物自动归档。触发词：有个想法、新需求、产品规划、写PRD、竞品分析、商业模式设计等。
agent_created: true
---

# 产品全链路工作流（Product Lifecycle）

从想法到落地的完整产品工作流，每一步都有结构化引导、虚拟角色审核和知识归档。

---

## 触发规则

本技能在以下场景触发：
- 用户提到"有个想法""新需求""产品规划""写PRD""竞品分析""商业模式设计"等产品工作关键词
- 用户使用 `/product-lifecycle` 命令
- 用户描述的产品工作场景匹配某个阶段

---

## 使用方式

### 子命令触发

| 命令 | 起始阶段 | 适用场景 |
|------|---------|---------|
| `/product-lifecycle brainstorm` | 阶段0 | 有个新想法，需要头脑风暴 |
| `/product-lifecycle discover` | 阶段1 | 收到一个需求，需要判别真伪 |
| `/product-lifecycle solution` | 阶段2 | 已有需求，需要设计方案 |
| `/product-lifecycle competitive` | 阶段3 | 需要做竞品分析 |
| `/product-lifecycle business` | 阶段4 | 需要设计商业模式 |
| `/product-lifecycle roadmap` | 阶段5 | 需要做战略规划和路线图 |
| `/product-lifecycle architecture` | 阶段6 | 需要设计平台架构 |
| `/product-lifecycle features` | 阶段7 | 需要设计产品功能 |
| `/product-lifecycle metrics` | 阶段8 | 需要设计指标和ROI |
| `/product-lifecycle deliver` | 阶段9 | 需要输出正式文档 |
| `/product-lifecycle project` | 阶段10 | 需要管理项目和需求池 |
| `/product-lifecycle full` | 全流程 | 从头走完整流程 |
| `/product-lifecycle review` | 审核模式 | 已有材料，需要虚拟角色审核 |

### 对话引导式

根据用户描述自动判断所处阶段：
- "我有个新想法" → 阶段0
- "帮我分析这个需求" → 阶段1
- "方案做好了帮我看看" → 审核模式
- "帮我写PRD" → 阶段9
- 其他场景根据上下文判断

---

## 全流程概览

```
阶段0  头脑风暴 & 想法孵化         输出：想法卡片
  ↓
阶段1  需求探索（真伪判别）         输出：需求判别报告       审核：用户视角
  ↓
阶段2  方案设计（至少2种）          输出：方案对比矩阵       审核：技术视角
  ↓
阶段3  竞品分析                   输出：竞品分析报告       审核：市场视角
  ↓
阶段4  商业模式 & 盈利设计         输出：商业模式画布        审核：CEO + 财务视角
  ↓
阶段5  战略规划 & 路线图           输出：产品路线图         审核：CEO视角
  ↓
阶段6  平台架构 & 开放API          输出：架构设计文档       审核：技术视角
  ↓
阶段7  功能设计 & 异常场景         输出：功能设计文档       审核：技术 + 用户视角
  ↓
阶段8  指标设计 & ROI测算          输出：指标体系 + ROI表   审核：财务视角
  ↓
阶段9  产物输出                   输出：PRD/RP/白皮书等    审核：CEO视角（最终）
  ↓
阶段10 项目管理 & 需求池           输出：项目计划 + 需求池
```

支持从任意阶段开始，无需顺序执行。若用户已有部分材料，直接从对应阶段继续。

---

## 虚拟审核角色

每个关键节点完成后，加载对应角色的审核引导文件，以该角色视角提出质疑和建议：

| 角色 | 视角 | 审核节点 | 引导文件 |
|------|------|---------|---------|
| CEO | 商业价值、战略对齐、资源投入 | 阶段4/5/9 | `references/reviewers/reviewer-ceo.md` |
| 用户 | 真实需求、体验流畅度、场景覆盖 | 阶段1/7 | `references/reviewers/reviewer-user.md` |
| 技术 | 可行性、架构合理性、技术债务 | 阶段2/6/7 | `references/reviewers/reviewer-tech.md` |
| 财务 | ROI、成本收益、商业模式可行性 | 阶段4/8 | `references/reviewers/reviewer-finance.md` |
| 合规 | 法律风险、隐私保护、行业合规 | 阶段4/7 | `references/reviewers/reviewer-legal.md` |
| 市场部 | 市场定位、竞品策略、传播策略 | 阶段3/5 | `references/reviewers/reviewer-marketing.md` |
| 运营部 | 运营可行性、用户增长、服务流程 | 阶段5/7/10 | `references/reviewers/reviewer-operations.md` |

审核方式：阅读对应审核角色文件后，以该角色视角对当前阶段产物提出3-5个关键问题，指出潜在风险和改进建议，由用户确认后再进入下一阶段。

---

## 执行流程

进入某个阶段时：

1. **加载阶段引导文件**：读取 `references/phase/phase-{N}-{name}.md`，按其中定义的引导问题与用户交互
2. **引导用户完成该阶段工作**：通过提问、讨论、分析等方式，帮助用户产出该阶段的交付物
3. **触发审核**：如果该阶段有对应的审核角色，加载审核文件并以该角色视角审核
4. **归档产物**：将产物保存到 `~/.workbuddy/products/{产品名称}/` 对应子目录
5. **确认下一阶段**：询问用户是否进入下一阶段或跳转到其他阶段

### 各阶段引导文件

| 阶段 | 文件路径 |
|------|---------|
| 阶段0 | `references/phase/phase-0-brainstorm.md` |
| 阶段1 | `references/phase/phase-1-discovery.md` |
| 阶段2 | `references/phase/phase-2-solution.md` |
| 阶段3 | `references/phase/phase-3-competitive.md` |
| 阶段4 | `references/phase/phase-4-business-model.md` |
| 阶段5 | `references/phase/phase-5-strategy-roadmap.md` |
| 阶段6 | `references/phase/phase-6-architecture.md` |
| 阶段7 | `references/phase/phase-7-feature-design.md` |
| 阶段8 | `references/phase/phase-8-metrics-roi.md` |
| 阶段9 | `references/phase/phase-9-delivery.md` |
| 阶段10 | `references/phase/phase-10-project.md` |

### 产物模板文件

输出正式文档时，参考 `assets/templates/` 下的模板：

| 产物 | 模板文件 |
|------|---------|
| PRD | `assets/templates/prd-template.md` |
| 解决方案 | `assets/templates/solution-template.md` |
| 竞品分析 | `assets/templates/competitive-analysis-template.md` |
| 商业模式 | `assets/templates/business-model-template.md` |
| 路线图 | `assets/templates/roadmap-template.md` |
| API设计 | `assets/templates/api-design-template.md` |
| 指标设计 | `assets/templates/metrics-design-template.md` |
| ROI测算 | `assets/templates/roi-template.md` |
| 项目计划 | `assets/templates/project-plan-template.md` |
| 白皮书 | `assets/templates/whitepaper-template.md` |

---

## 产物归档

每个阶段完成后，产物归档到：

```
~/.workbuddy/products/{产品名称}/
├── 00-ideas/           # 想法卡片
├── 01-discovery/       # 需求判别
├── 02-solutions/       # 方案设计
├── 03-competitive/     # 竞品分析
├── 04-business/        # 商业模式
├── 05-strategy/        # 战略规划
├── 06-architecture/    # 架构设计
├── 07-features/        # 功能设计
├── 08-metrics/         # 指标设计
├── 09-deliverables/    # 最终产物（PRD/RP/白皮书等）
└── 10-project/         # 项目管理
```

输出格式策略：
- 工作过程文档（想法卡片/需求判别/方案对比等）→ Markdown
- 正式交付物（PRD/白皮书/解决方案等）→ Word (.docx)，使用 minimax-docx 技能生成
- RP原型 → 交互式 HTML 原型（可在浏览器预览）

---

## 首次使用

1. 询问用户产品名称，创建归档目录
2. 判断用户当前所处阶段（通过子命令或对话推断）
3. 加载对应阶段的引导文件，开始引导
4. 每个阶段完成后自动归档，询问是否继续下一阶段
