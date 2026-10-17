# Smoke Test — 2026-10-17

## 结构检查

| 检查项 | 结果 | 证据 |
|---|---|---|
| frontmatter name | 通过 | `ai-code-review-queue-designer` 符合 lowercase-hyphen |
| description | 通过 | 147 字符；以 Designs 开头，说明触发条件 |
| 必要章节 | 通过 | 包含 核心定位、触发场景、工作流、输出格式、Gotchas |
| 工作流 | 通过 | 6 个步骤，符合 3–8 步要求 |
| Gotchas | 通过 | 6 条，均含可操作约束 |
| 占位符 | 通过 | 未发现未填充模板字段 |
| README 一致性 | 通过 | 英文安装路径、仓库名、文件树及触发词均与 Skill 名一致 |

## 触发干运行

### 中文触发词

输入：`我们 AI 写的 PR 变多了，支付和 CI 哪些必须人工看？请给两周试点做审查分流。`

预期路由：触发本 Skill，输出风险矩阵，将支付和 CI 设为高风险，要求人工席位、自动证据、回滚与试点指标；不直接合并或替代安全审计。

结果：通过。输入同时包含 AI 辅助变更、人工审批、敏感路径和试点要求，能自然进入 Step 1–6 并生成可执行队列包。

### English / variation trigger

Input: `Design approval gates and a rollback-ready review queue for agent-generated pull requests in our release repository.`

Expected routing: trigger this Skill; collect repository constraints, classify release paths as high risk, require human approvals and a validated rollback path.

Result: passed. The request matches the stated AI code-change, approval routing, evidence, and rollback scope rather than a generic bug review.

## 结论

**通过。** 发布前结构、README 和两条触发干运行均通过；干运行是路由与输出契约检查，不声称已验证任何实际仓库权限或生产回滚。
