# Agent 编排

## 可用的 Agents

位于 `~/.claude/agents/`：

| Agent | 用途 | 何时使用 |
|-------|---------|-------------|
| planner | 实施规划 | 复杂功能、重构 |
| architect | 系统设计 | 架构决策 |
| tdd-guide | 测试驱动开发 | 新功能、bug 修复 |
| code-reviewer | 代码审查 | 编写代码后 |
| security-reviewer | 安全分析 | 提交前 |
| build-error-resolver | 修复构建错误 | 构建失败时 |
| e2e-runner | E2E 测试 | 关键用户流程 |
| refactor-cleaner | 清理死代码 | 代码维护 |
| doc-updater | 文档更新 | 更新文档 |

## 立即使用 Agent

无需用户提示：
1. 复杂功能请求 - 使用 **planner** agent
2. 刚刚编写/修改的代码 - 使用 **code-reviewer** agent
3. Bug 修复或新功能 - 使用 **tdd-guide** agent
4. 架构决策 - 使用 **architect** agent

## 并行任务执行

始终对独立操作使用并行 Task 执行：

```markdown
# 好的做法：并行执行
同时启动 3 个 agents：
1. Agent 1: auth 模块的安全分析
2. Agent 2: 缓存系统的性能审查
3. Agent 3: 工具函数的类型检查

# 不好的做法：不必要的顺序执行
先 agent 1，然后 agent 2，然后 agent 3
```

## 多角度分析

对于复杂问题，使用分角色子 agents：
- 事实审查员
- 高级工程师
- 安全专家
- 一致性审查员
- 冗余检查员
