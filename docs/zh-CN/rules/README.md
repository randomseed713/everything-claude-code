# Rules（规则）

## 结构

规则分为 **common**（通用）层以及 **特定语言** 目录：

```
rules/
├── common/          # 语言无关的原则（始终安装）
│   ├── coding-style.md
│   ├── git-workflow.md
│   ├── testing.md
│   ├── performance.md
│   ├── patterns.md
│   ├── hooks.md
│   ├── agents.md
│   └── security.md
├── typescript/      # TypeScript/JavaScript 专用
├── python/          # Python 专用
└── golang/          # Go 专用
```

- **common/** 包含通用原则 — 不包含特定语言的代码示例。
- **语言目录** 扩展了通用规则，添加了特定框架的模式、工具和代码示例。每个文件都会引用其对应的 common 文件。

## 安装

### 选项 1：安装脚本（推荐）

```bash
# 安装 common + 一个或多个特定语言规则集
./install.sh typescript
./install.sh python
./install.sh golang

# 一次性安装多个语言
./install.sh typescript python
```

### 选项 2：手动安装

> **重要：** 复制整个目录 — 不要使用 `/*` 扁平化。
> Common 和特定语言目录包含同名文件。
> 将它们扁平化到一个目录会导致特定语言文件覆盖
> common 规则，并破坏特定语言文件使用的相对路径 `../common/` 引用。

```bash
# 安装 common 规则（所有项目都需要）
cp -r rules/common ~/.claude/rules/common

# 根据项目技术栈安装特定语言规则
cp -r rules/typescript ~/.claude/rules/typescript
cp -r rules/python ~/.claude/rules/python
cp -r rules/golang ~/.claude/rules/golang

# 注意！！！请根据您的实际项目需求进行配置；此处配置仅供参考。
```

## Rules vs Skills（规则 vs 技能）

- **Rules（规则）** 定义广泛适用的标准、约定和检查清单（例如，"80% 测试覆盖率"、"不要硬编码密钥"）。
- **Skills（技能）**（`skills/` 目录）为特定任务提供深入的、可操作的参考材料（例如，`python-patterns`、`golang-testing`）。

特定语言的规则文件会在适当的地方引用相关技能。规则告诉你 *要做什么*；技能告诉你 *如何做*。

## 添加新语言

要添加对新语言的支持（例如 `rust/`）：

1. 创建 `rules/rust/` 目录
2. 添加扩展 common 规则的文件：
   - `coding-style.md` — 格式化工具、惯用法、错误处理模式
   - `testing.md` — 测试框架、覆盖率工具、测试组织
   - `patterns.md` — 特定语言的设计模式
   - `hooks.md` — 用于格式化器、linter、类型检查器的 PostToolUse hooks
   - `security.md` — 密钥管理、安全扫描工具
3. 每个文件应该以以下内容开头：
   ```
   > This file extends [common/xxx.md](../common/xxx.md) with <Language> specific content.
   ```
4. 如果有可用的技能，请引用现有技能，或在 `skills/` 下创建新技能。
