# Go 测试

> 本文件使用 Go 专用内容扩展了 [common/testing.md](../common/testing.md)。

## 框架

使用标准 `go test` 配合 **table-driven tests（表驱动测试）**。

## Race 检测

始终使用 `-race` 标志运行：

```bash
go test -race ./...
```

## 覆盖率

```bash
go test -cover ./...
```

## 参考

参见 skill：`golang-testing` 了解详细的 Go 测试模式和辅助函数。
