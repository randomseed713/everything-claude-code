# Go 编码风格

> 本文件使用 Go 专用内容扩展了 [common/coding-style.md](../common/coding-style.md)。

## 格式化

- **gofmt** 和 **goimports** 是强制性的 — 没有风格争议

## 设计原则

- 接受 interfaces，返回 structs
- 保持 interfaces 小巧（1-3 个方法）

## 错误处理

始终用上下文包装错误：

```go
if err != nil {
    return fmt.Errorf("failed to create user: %w", err)
}
```

## 参考

参见 skill：`golang-patterns` 了解全面的 Go 惯用法和模式。
