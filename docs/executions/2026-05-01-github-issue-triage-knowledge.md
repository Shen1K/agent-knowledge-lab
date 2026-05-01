# GitHub Issue 分诊知识用例执行文档

日期：2026-05-01

## 目的

使用 Agent Knowledge Lab 自身，围绕 GitHub Issue 分诊建立一份真实的领域知识。

这不是单纯的项目说明文档，而是一次 reference use case：用它来检验当前知识体系是否真的能支持知识生成、记录、迭代和反馈。

## 初始思考

项目现在已经有模板、原则、schema 和一个教学示例，但这些仍然主要是“设计出来的结构”。这次执行应该把结构放到真实材料和公开维护者实践中受压，看看它是否能产出真正可用的知识。

第一份有价值的知识不应该一上来就是完整的分诊 SOP。更合理的是先抓住一个前置判断，因为它会影响后面很多分诊决策：

> 这个 issue 的信息是否足够支持下一步分诊判断？

## 初始假设

- 公开维护者指南可以作为第一轮信息来源，但证据强度弱于真实 issue 历史样本。
- AI 生成的知识产物应保持 `status: hypothesis`。
- 第一组产物至少应该包括 raw source notes、一个 case card、一个 claim、一个 decision point、一个 playbook 和一个 eval。
- 这次 use case 应该反向暴露 Agent Knowledge Lab 自身的设计问题。
- 完成条件不是“写出一篇知识文档”，而是仓库中出现一组连贯的知识切片、一份过程记录，以及一条项目级反馈。

## 初始完成条件

- 证据来源被记录，并拥有稳定 ID 和链接。
- `knowledge/03-claims/github-issue-triage` 下存在真实领域 claim。
- claim 与 decision point、playbook、eval 和 source notes 形成关联。
- 这份知识既能被人通过 Obsidian/Markdown 理解，也能被 agent 通过 frontmatter 使用。
- 执行文档记录我的假设如何变化。
- 项目的 self-audit 或 roadmap 记录这次 use case 暴露出的设计反馈。

## 执行日志

### 2026-05-01 12:55 - 开始

我先写执行文档，再创建知识产物。这是刻意的：文档应该捕捉执行过程中的真实推理路径，而不是最后补写一份漂亮总结。

当前假设：相比直接做通用 issue labeling，“信息充分性判断”更适合作为第一个知识目标，因为它位于 bug / feature / duplicate / module routing 等判断之前。

### 2026-05-01 13:05 - 搜集来源

我搜索并阅读了 GitHub Docs、Kubernetes、VS Code、Rust、Chatwoot 和 StackBlitz 的公开资料。

来自来源的反馈：

- 初始假设变强了。多个项目都把“缺少信息”视为早期分诊状态。
- 标签词汇并不统一：公开资料中出现了 `needs more info`、`triage/needs-information`、`S-needs-info`、`S-needs-repro`、`need-more-info` 等不同表达。
- 可迁移的知识不是某个具体 label 名称，而是一个判断模式：在做更强分类、路由、关闭或 duplicate 判断之前，先判断这个 issue 是否 actionable。
- 暴露出一个隐藏 schema 需求：证据应记录 `source_type` 和粗粒度 `evidence_strength`，因为 official docs、project handbooks、真实 issue 样本不应该被同等对待。

执行动作：

- 创建 raw source notes：`knowledge/01-raw/github-issue-triage/source-notes-github-issue-information-sufficiency.md`。

### 2026-05-01 13:15 - 建立案例卡

我从公开项目实践中创建了两个 case cards：

- `case-vscode-needs-more-info-loop`
- `case-rust-needs-repro-and-duplicate-caution`

思考：

- VS Code 有价值，因为它体现了“缺少信息”是一种会阻塞后续流程的状态。
- Rust 有价值，因为它把 needs-repro 和 duplicate confidence 区分开，能避免 agent 把不同问题过度合并。

调整：

- 原计划中 case card 应该重建“人类活动事件”。但公开维护者指南不是单个历史事件，而是重复活动模式的描述。这暴露出一个设计问题：项目是否应该区分 `case_card` 和 `practice_case`？

当前决策：

- 暂时仍使用 `case_card`，但把这个问题记录为后续项目反馈。

### 2026-05-01 13:30 - 生成知识产物

我创建了第一组真实知识切片：

- Claim：`claim-github-issue-info-sufficiency-before-classification`
- Decision point：`dp-github-issue-triage-information-sufficiency`
- Playbook：`playbook-github-issue-info-first-triage`
- Eval：`eval-github-issue-info-request-usefulness`

思考：

- claim 是最小的可证伪知识主张。
- decision point 是任务中真正使用 claim 的判断点。
- playbook 是可执行的任务包装。
- eval 描述未来反馈如何判断这份知识是否有用。

调整：

- 我没有复用 `examples/` 中已有的 ID，因为重复 ID 会让知识图谱、检索和迁移变得模糊。这暴露出一个项目问题：examples 和真实 knowledge 需要独立命名空间，或者示例 ID 应该有显式前缀。

当前置信度：

- claim 的 confidence 保持为 `0.72`，但没有升级为 validated。公开指南足以形成较强假设，但还不足以证明真实执行效果。

### 2026-05-01 13:45 - 项目反馈与调整

这次 use case 暴露出三个项目级缺口：

1. 没有 source-notes 模板，但在写 claim 之前，来源归一化是必要步骤。
2. knowledge claim 模板没有显式记录 `evidence_strength`。
3. knowledge claim 模板没有显式记录 `transferability`，但通用、领域、项目、工具层知识的区别马上就变得重要。

执行中的调整：

- 新增 `skill/templates/source-notes.md`。
- 更新 `skill/SKILL.md`。
- 更新 `skill/templates/knowledge-claim.md`。
- 更新 `schemas/knowledge-claim.schema.json`。
- 给新的 GitHub Issue triage claim 增加 `evidence_strength: medium` 和 `transferability: domain`。
- 新增 change proposal：`knowledge/08-changes/change-github-issue-triage-use-case-design-feedback.md`。

这第一次具体证明：reference use case 不应该只产出领域知识，它也应该反过来改进知识系统本身。

### 2026-05-01 14:00 - 一致性检查

我更新了教学示例 claim，让它也包含 `evidence_strength` 和 `transferability`，避免 schema 已更新但示例落后的问题。

我也更新了 knowledge map，这样人类在 Obsidian 中打开 vault 时，不需要手动浏览文件夹，就能找到第一组真实知识切片。

项目 self-audit 新增记录了三个风险：

- 来源证据被打平。
- examples 和真实 knowledge 可能共享 ID。
- 公开 practice guides 不等同于单个真实 case。

这强化了一个设计原则：reference use case 应该同时产出领域产物和方法反馈。

### 2026-05-01 14:10 - 验证

执行的检查：

- JSON schemas 可以正常解析。
- `evidence_strength` 和 `transferability` 已出现在模板、schema、真实 claim 和教学示例中。
- 第一组真实知识切片已列入 `knowledge/00-index/knowledge-map.md`。
- 简单 ID 扫描没有发现新建真实知识产物之间存在重复 ID。

反馈：

- 仓库目前还缺少真正的 Markdown/frontmatter validator。对第一次 use case 来说，手动检查和 grep 足够；但多人贡献或知识数量增长后，这不够。
- 未来 Knowledge Agent 需要一个自动验证器，检查：
  - 重复 ID
  - 缺失必填 frontmatter
  - 失效的 `[[wiki links]]`
  - 不支持的 relation types
  - 没有 evaluation section 的 claims
  - 缺少强证据却被标记为 validated 的 claims

更新后的完成条件评估：

- 证据来源已记录：是。
- 真实 claim 已创建：是。
- claim 已连接 decision point、playbook、eval 和 source notes：是。
- 人类可读且 frontmatter 可读：是。
- 执行推理已边做边记录：是。
- 项目级设计反馈已记录：是。
- 剩余限制：还没有使用真实 issue-history 样本做验证。
