# AI代码审查队列设计师 · AI Code Review Queue Designer

为 AI 辅助研发团队设计按风险分流的代码审查队列：自动检查做广覆盖，人工注意力留给真正高风险的决策。

## 用途

它将仓库变更分类为低、中、高风险，并生成审批席位、证据清单、复审上限、合并条件和回滚准备度。它不执行合并，也不替代安全审计或缺陷审查。

## 触发词

- “帮我给 AI 生成代码建立 PR 审查分流规则”
- “代码变更多了，哪些必须人工 review？”
- “Design a risk-based review queue for AI-assisted pull requests.”
- “Set approval and rollback rules for our agent-generated changes.”

## 工作流

`收集边界 → 风险分层 → 编排审查队列 → 设置收敛升级 → 定义回滚试点 → 输出队列包`

## 输出

- 风险路由矩阵
- PR 证据清单与审批规则
- 复审收敛和升级条件
- 回滚准备度要求
- 试点指标与 GO / CHECK / NO-GO 结论

## 示例

输入：`我们每周有 80 个 AI 辅助 PR，支付和 CI 不能漏审。帮我做一个两周试点的审查队列。`

输出会把支付、CI、认证和发布文件默认列为高风险，要求两个人工席位和路径所有者；普通业务逻辑要求一人审批；文档或隔离测试在自动检查与证据完整时可快速放行，并同时给出回滚和指标采集方案。

## 安装与发布

安装目录使用英文 skill 名，而不是本机显示用的中文目录名：

```text
~/.claude/skills/ai-code-review-queue-designer/SKILL.md
```

仓库建议名：`ai-code-review-queue-designer`。将本目录提交到一个新的 GitHub 仓库即可；发布前请先阅读并通过 `smoke-test.md`。

## 文件树

```text
ai-code-review-queue-designer/
├── SKILL.md
├── README.md
├── smoke-test.md
└── publish-checklist.md
```

## 注意

规则必须由实际仓库权限、发布流程和代码所有者制度校准。没有验证的回滚路径时，结论不得写成 GO。
