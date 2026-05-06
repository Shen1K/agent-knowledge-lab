# 知识生成 Skill

当你需要把原始材料转化为人类和 AI Agent 都能使用的知识时，使用这个 skill。

## 目标

从文档、数据、图片、issue、聊天记录或执行轨迹中生成结构化、可证伪、可维护的知识。

不要直接从原始材料跳到最终规则。先重建人类活动，再提出知识。

## 工作流

1. **收集原始材料**
   保留原始材料或指向它的稳定引用。不要把证据直接改写成知识。

   当原始材料来自多个公开来源时，先创建 source notes，再创建 claims。Source notes 应记录来源类型、观察到的模式、相关性、限制和证据强度。

2. **重建活动**
   对每个相关片段，识别：
   - actor
   - goal
   - object
   - context
   - constraints
   - judgment
   - action
   - tool
   - result
   - evaluation signal

3. **创建案例卡**
   把重要片段转化为案例卡。案例卡应该描述发生了什么，而不是宣称永远应该怎么做。

4. **比较案例**
   寻找重复出现的判断、行动、成功与失败差异、缺失信息、例外和专家行为。

5. **提出知识主张**
   Claim 是一个有范围、有证据、可使用、可证伪的陈述。AI 生成的 claim 默认 `status: hypothesis`。

6. **附加边界**
   对每个 claim，说明它什么时候适用、什么时候不适用，以及已知反例。

7. **连接知识**
   添加 `depends_on`、`supports`、`conflicts_with`、`generalizes`、`specializes` 和 `derived_from` 等关系。

8. **定义评估**
   每个可行动的 claim 都应该说明未来如何测试或观察它是否有效。

9. **生成变更提案**
   更新已有知识时，用理由和证据提出变更。不要静默覆盖已验证知识。

## 输出规则

- 优先使用带 YAML frontmatter 的 Markdown。
- 使用稳定 ID。
- 在面向人类的章节中使用 Obsidian 风格的 `[[wiki links]]`。
- 把机器可读元数据保留在 frontmatter 中。
- 在正文中保留人类解释、示例和反例。
- 区分 hypothesis、reviewed、validated、conflicted 和 deprecated 知识。
- 当公开指南、issue 样本、论文和维护者评论混合使用时，区分来源类型和证据强度。

## 默认状态

```text
hypothesis: AI 生成或证据较弱。
reviewed: 人类已检查 claim 的合理性。
validated: 有证据、评估或反复成功使用支持。
conflicted: 被另一个 claim 或 case 反驳。
deprecated: 不再推荐使用。
```

## 最小知识主张

一个最小 claim 必须包含：

- id
- type
- title
- scope
- status
- claim
- evidence
- evidence_strength
- transferability
- applies_when
- does_not_apply_when
- agent_use
- human_explanation
- evaluation

## 反模式

- 把总结当成知识。
- 在没有证据的情况下，把模型输出升级为事实。
- 写没有边界的规则。
- 写人类无法理解的 Agent-only 指令。
- 写 Agent 无法使用的 Human-only 文章。
- 添加模糊的 `related` 链接，而不是有意义的关系类型。
