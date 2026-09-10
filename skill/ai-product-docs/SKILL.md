---
name: ai-product-docs
description: 为 AI 产品项目创建、补全、更新或审计一套固定的 16 份标准文档，包括竞品、立项、产品与功能需求、埋点、模型评测与选型、Agent 需求、测试、用户研究和数据大盘分析。适用于用户要求生成其中一份、多份、整套文档或检查跨文档一致性时。
---

# AI 产品项目文档包

将 16 份文档视为同一项目知识库的不同视图。先建立共享事实，再生成具体文档；不要让各文档各自猜测项目背景、指标或功能定义。

## 工作模式

根据请求选择最小充分模式：

- **建立目录**：输出文档清单、用途、依赖、状态和建议生成顺序。读取 [document-catalog.md](references/document-catalog.md)。
- **项目建档**：整理用户材料为共享项目事实库。读取 [shared-project-context.md](references/shared-project-context.md)。
- **生成文档**：只读取所请求文档对应的模板；需要依赖信息时再读取上游模板。
- **批量生成**：先建项目事实库，然后依照目录中的顺序生成。尚无运行数据的评测报告、评测修改和数据大盘分析，先生成“待执行版”，不要虚构结果。
- **更新文档**：保留未被新证据推翻的内容，更新版本、变更记录和受影响的关联文档。
- **一致性审计**：读取 [quality-and-consistency.md](references/quality-and-consistency.md)，检查事实、ID、指标口径、版本和追踪链。

## 必须遵守的约束

1. 区分四种内容：`事实`、`证据支持的判断`、`假设`、`待确认`。不得把假设写成事实。
2. 缺少信息时使用 `TBD（待确认：具体问题）`，并在文末集中列出待确认项；不要用编造内容填满模板。
3. 所有关键项使用稳定 ID。默认前缀见共享项目事实库；已有项目编号体系时沿用用户体系。
4. 每个结论尽可能标注来源。外部资料记录标题、链接、发布日期与访问日期；用户提供材料标明文件名或访谈编号。
5. 对 AI 能力同时覆盖质量、延迟、成本、稳定性、安全与可观测性，不能只写功能描述。
6. 对 Agent 明确工具权限、数据边界、失败降级、人工介入和审计要求。
7. 所有指标写清公式、统计粒度、时间窗口、数据源、过滤规则与目标值；无法确定时标为 TBD。
8. 表格中的“一行”必须代表一种稳定对象，不混合多个事件、需求、用例或测试意图。
9. 默认输出中文，保留必要英文术语并首次给出中文解释。用户指定语言、格式或组织模板时，以用户要求为准。

## 生成流程

1. 读取用户材料，提取事实、来源、未知项和冲突项。
2. 建立或更新共享项目事实库，包括术语表、目标指标、功能清单、风险、来源登记和版本信息。
3. 确认用户要一份、多份还是整套文档。用户已明确时不要重复询问。
4. 读取对应模板并生成内容。批量生成时使用目录中的建议顺序。
5. 建立跨文档追踪：用户/用例 → 功能/需求 → 埋点/测试 → 评测/指标 → 结论/行动。
6. 执行轻量质量检查，输出已完成内容、关键假设、待确认项和后续可执行动作。

## 输出与文件规则

- 默认使用 Markdown；表格需具备稳定列名并可直接迁移到 Excel。
- 用户要求 Word、Excel 或其他办公格式时，使用环境中可用的文档或表格能力生成原生文件；同一文档不要同时维护两份事实源。
- 默认文件名采用目录中的编号与中文名称，确保自然排序。
- 单份文档开头至少包含：项目名、文档状态、版本、负责人、创建/更新时间、输入来源。
- 单份文档结尾至少包含：结论或决策、风险、待确认项、变更记录。

## 模板路由

1. [竞品分析横向竞品](references/templates/01-horizontal-competitor-analysis.md)
2. [竞品分析纵向竞品](references/templates/02-longitudinal-competitor-analysis.md)
3. [立项报告](references/templates/03-project-initiation-report.md)
4. [产品设计文档](references/templates/04-product-design-document.md)
5. [功能需求文档](references/templates/05-functional-requirements-document.md)
6. [数据埋点表](references/templates/06-tracking-plan.md)
7. [模型评测——评测集](references/templates/07-model-evaluation-dataset.md)
8. [模型评测——评测修改](references/templates/08-model-evaluation-changelog.md)
9. [模型评测——评测指标](references/templates/09-model-evaluation-metrics.md)
10. [模型评测——评测报告](references/templates/10-model-evaluation-report.md)
11. [模型选型表](references/templates/11-model-selection-matrix.md)
12. [Agent需求文档](references/templates/12-agent-requirements-document.md)
13. [测试case表](references/templates/13-test-cases.md)
14. [用户用例集（表格显示）](references/templates/14-user-use-cases.md)
15. [用户分析报告](references/templates/15-user-analysis-report.md)
16. [数据大盘分析](references/templates/16-dashboard-analysis.md)
