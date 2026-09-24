# AI Product Docs Skill

一套面向 AI 产品项目的 Codex Skill，用于创建、补全、更新和审计 16 份标准项目文档。

它不只是提供 16 个空白模板，而是先建立共享项目事实，再让用户研究、竞品、立项、需求、埋点、模型评测、Agent、测试和数据分析使用同一套术语、指标与追踪关系，减少文档之间互相矛盾的问题。

## 能做什么

- 生成单份、多份或整套 AI 产品项目文档。
- 把零散材料整理成可复用的项目事实库。
- 区分事实、证据支持的判断、假设与待确认项，避免用编造内容填满模板。
- 使用稳定 ID 串联用户、用例、功能、需求、埋点、测试、评测、决策与行动。
- 检查跨文档的事实、术语、版本、指标口径和追踪关系是否一致。
- 覆盖 AI 产品特有的质量、延迟、成本、稳定性、安全、可观测性，以及 Agent 的工具权限、失败降级和人工介入。

## 16 份标准文档

| 阶段 | 文档 |
|---|---|
| 机会研究 | 01 横向竞品分析、02 纵向竞品分析、15 用户分析报告 |
| 立项与方案 | 03 立项报告、04 产品设计文档、14 用户用例集 |
| 需求与数据 | 05 功能需求文档、06 数据埋点表 |
| 模型评测与选型 | 07 评测集、08 评测修改、09 评测指标、10 评测报告、11 模型选型表 |
| Agent 与测试 | 12 Agent 需求文档、13 测试 Case 表 |
| 上线运营 | 16 数据大盘分析 |

每份文档的用途、默认文件名、依赖与推荐生成顺序见 [DOCUMENT_CATALOG.md](DOCUMENT_CATALOG.md)。

## 工作方式

```text
项目资料
  → 共享项目事实库
  → 按依赖生成所需文档
  → 建立跨文档追踪链
  → 执行质量与一致性检查
```

默认追踪链为：

```text
SEG / INS → UC → F / REQ → EVT / TC → EVAL / MET → RUN → DEC / ACT
```

当缺少真实评测或线上运行数据时，Skill 会生成“待执行版”结构、数据需求与验收门槛，不会虚构评测分数、用户结论或大盘分析结果。

## 安装

仓库本身不需要安装运行依赖。将 `skill/ai-product-docs` 目录复制或软链接到 Codex 的用户级 Skill 目录 `$HOME/.agents/skills` 即可。

以下是在 macOS 或 Linux 上使用软链接的示例：

```bash
git clone https://github.com/yuling170916/ai-product-docs-skill.git
cd ai-product-docs-skill
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skill/ai-product-docs" "$HOME/.agents/skills/ai-product-docs"
```

Codex 会自动检测 Skill 变更；如果新安装的 Skill 没有出现，请重启 Codex。需要只在某个仓库中使用时，也可以将 Skill 放到该仓库的 `.agents/skills/` 目录。

## 使用

在 Codex 中直接点名 `$ai-product-docs`，并提供项目资料、所需文档和输出要求。

### 生成单份文档

```text
使用 $ai-product-docs，根据下面的项目资料生成 03 立项报告。
未知信息不要猜，统一标记为 TBD，并列出需要我补充的问题。

项目资料：……
```

### 生成整套文档

```text
使用 $ai-product-docs，为这个 AI 客服项目建立共享事实库，
再按推荐顺序生成完整的 16 份文档。没有真实运行数据的部分先生成待执行版。

项目资料：……
```

### 审计现有文档

```text
使用 $ai-product-docs，审计这些文档之间的事实、ID、指标口径、版本和追踪关系，
按优先级列出冲突、缺口、影响范围和建议修改。
```

为了得到更可靠的结果，建议至少提供：项目目标、目标用户、核心场景、当前阶段、范围与非目标、已有数据或研究、关键约束，以及希望交付的文档范围。

## 仓库结构

```text
ai-product-docs-skill/
├── README.md
├── DOCUMENT_CATALOG.md
└── skill/
    └── ai-product-docs/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── document-catalog.md
            ├── shared-project-context.md
            ├── quality-and-consistency.md
            └── templates/
                └── 01–16 共 16 份详细模板
```

## 设计原则

1. 先统一事实，再写具体文档。
2. 结论尽可能能追溯到来源，不把假设写成事实。
3. 关键对象使用稳定 ID，保证上下游可追踪。
4. 指标必须包含公式、粒度、窗口、数据源、过滤规则与目标值。
5. AI 能力同时考虑质量、延迟、成本、稳定性与安全。
6. Agent 的自主动作必须说明权限、失败策略、审计和人工介入。

## 相关资料

- [完整文档目录](DOCUMENT_CATALOG.md)
- [Skill 主说明](skill/ai-product-docs/SKILL.md)
- [OpenAI 官方 Codex Skill 构建说明](https://learn.chatgpt.com/docs/build-skills)

## 许可证

本仓库当前未包含开源许可证。公开可见不等于已授权复制、修改或分发；如计划开放复用，建议后续补充明确的 `LICENSE`。
