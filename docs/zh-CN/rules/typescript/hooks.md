# TypeScript/JavaScript Hooks

> 本文件使用 TypeScript/JavaScript 专用内容扩展了 [common/hooks.md](../common/hooks.md)。

## PostToolUse Hooks

在 `~/.claude/settings.json` 中配置：

- **Prettier**: 编辑后自动格式化 JS/TS 文件
- **TypeScript check**: 编辑 `.ts`/`.tsx` 文件后运行 `tsc`
- **console.log warning**: 警告已编辑文件中的 `console.log`

## Stop Hooks

- **console.log audit**: 在会话结束前检查所有已修改文件中的 `console.log`
