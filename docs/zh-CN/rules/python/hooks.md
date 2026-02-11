# Python Hooks

> 本文件使用 Python 专用内容扩展了 [common/hooks.md](../common/hooks.md)。

## PostToolUse Hooks

在 `~/.claude/settings.json` 中配置：

- **black/ruff**: 编辑后自动格式化 `.py` 文件
- **mypy/pyright**: 编辑 `.py` 文件后运行类型检查

## 警告

- 警告已编辑文件中的 `print()` 语句（改用 `logging` 模块）
