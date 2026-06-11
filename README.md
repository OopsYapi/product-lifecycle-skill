# product-lifecycle-skill

产品全链路工作流技能（Product Lifecycle Skill），适用于 WorkBuddy / CodeBuddy。

覆盖从「有个想法」到「产品落地」的完整工作流，在关键节点引入 7 个虚拟角色审核，产物自动归档。

## 功能概览

| 阶段 | 内容 | 审核角色 |
|------|------|---------|
| 阶段0 | 头脑风暴 / 想法孵化 | — |
| 阶段1 | 需求探索 / 真伪需求判别 | 用户视角 |
| 阶段2 | 方案设计（至少 2 种方案） | 技术视角 |
| 阶段3 | 竞品分析 | 市场部视角 |
| 阶段4 | 商业模式 / 盈利模式设计 | CEO + 财务视角 |
| 阶段5 | 战略规划 / 产品路线图 | CEO + 市场部视角 |
| 阶段6 | 平台架构 / 开放 API 设计 | 技术视角 |
| 阶段7 | 功能设计 / 异常场景设计 | 用户 + 技术 + 合规视角 |
| 阶段8 | 指标设计 / ROI 测算 | 财务视角 |
| 阶段9 | 产物输出（PRD/白皮书/解决方案） | CEO 视角 |
| 阶段10 | 项目管理 / 需求池管理 | 运营部视角 |

## 虚拟审核角色（7 个）

- 👤 **用户视角** — 质疑真实需求、体验流畅度
- 🎯 **CEO 视角** — 商业价值、战略对齐、资源投入
- 🔧 **技术视角** — 可行性、架构合理性、技术债务
- 💰 **财务视角** — ROI、成本收益、商业模式可行性
- ⚖️ **合规视角** — 法律风险、隐私保护、行业合规
- 📢 **市场部视角** — 市场定位、竞品策略、传播策略
- 📋 **运营部视角** — 运营可行性、用户增长、服务流程

## 安装方法

### 方式一：从 Release 下载（推荐）

1. 前往 [Releases](https://github.com/OopsYapi/product-lifecycle-skill/releases) 下载最新版的 `product-lifecycle-skill.tar.gz`
2. 解压到 WorkBuddy 技能目录：
   ```bash
   tar -xzf product-lifecycle-skill.tar.gz -C ~/.workbuddy/skills/
   ```
3. 重启 WorkBuddy，技能自动生效

### 方式二：从源码安装

```bash
git clone https://github.com/OopsYapi/product-lifecycle-skill.git
cp -r product-lifecycle-skill ~/.workbuddy/skills/product-lifecycle
```

### 方式三：在 WorkBuddy 中安装

在 WorkBuddy 对话中输入：
```
/install-skill ~/.workbuddy/skills/product-lifecycle/
```

## 使用方法

安装后，在 WorkBuddy 对话中直接说：

- "我有个新想法" → 自动进入阶段 0（头脑风暴）
- "帮我分析这个需求" → 自动进入阶段 1（需求判别）
- "写一份 PRD" → 自动进入阶段 7（功能设计）→ 阶段 9（产物输出）
- `/product-lifecycle brainstorm` → 从头脑风暴开始
- `/product-lifecycle full` → 完整流程引导

## 产物输出

每个阶段的产物自动归档到 `~/.workbuddy/products/{产品名称}/`：

```
~/.workbuddy/products/停车信用服务平台/
├── 01-想法卡片.md
├── 02-需求判别报告.md
├── 03-解决方案对比.md
├── 04-竞品分析报告.md
├── 05-商业模式设计.md
├── 06-战略规划与路线图.md
├── 07-产品架构设计.md
├── 08-功能设计与异常场景.md
├── 09-指标设计与ROI测算.md
├── 10-PRD-产品需求文档.docx
├── 10-产品白皮书.docx
└── 11-项目管理与需求池.md
```

## 目录结构

```
product-lifecycle/
├── SKILL.md                    # 技能主入口
├── references/
│   ├── phase/                  # 11 个阶段引导文件
│   │   ├── phase-0-brainstorm.md
│   │   ├── phase-1-discovery.md
│   │   └── ...
│   └── reviewers/             # 7 个审核角色文件
│       ├── reviewer-user.md
│       ├── reviewer-ceo.md
│       └── ...
└── assets/
    └── templates/             # 10 个产物模板
        ├── prd-template.md
        └── ...
```

## 技能来源

本技能由 AI 辅助创建，覆盖产品经理从想法到落地的完整工作流。

## License

MIT
