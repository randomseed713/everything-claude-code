# 性能优化

## Model 选择策略

**Haiku 4.5**（Sonnet 能力的 90%，成本节省 3 倍）：
- 频繁调用的轻量级 agents
- 结对编程和代码生成
- 多 agent 系统中的 worker agents

**Sonnet 4.5**（最佳编码模型）：
- 主要开发工作
- 编排多 agent 工作流
- 复杂编码任务

**Opus 4.5**（最深推理）：
- 复杂架构决策
- 最大推理需求
- 研究和分析任务

## Context Window 管理

避免在以下情况使用 context window 的最后 20%：
- 大规模重构
- 跨多个文件的功能实现
- 调试复杂交互

Context 敏感度较低的任务：
- 单文件编辑
- 独立工具创建
- 文档更新
- 简单 bug 修复

## Extended Thinking + Plan Mode

Extended thinking 默认启用，为内部推理保留最多 31,999 个 tokens。

控制 extended thinking：
- **切换**: Option+T (macOS) / Alt+T (Windows/Linux)
- **配置**: 在 `~/.claude/settings.json` 中设置 `alwaysThinkingEnabled`
- **预算上限**: `export MAX_THINKING_TOKENS=10000`
- **详细模式**: Ctrl+O 查看 thinking 输出

对于需要深度推理的复杂任务：
1. 确保 extended thinking 已启用（默认开启）
2. 启用 **Plan Mode** 以采用结构化方法
3. 使用多轮批评进行彻底分析
4. 使用分角色子 agents 获得多样化视角

## 构建故障排除

如果构建失败：
1. 使用 **build-error-resolver** agent
2. 分析错误消息
3. 增量修复
4. 每次修复后验证
