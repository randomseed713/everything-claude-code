# Go 安全

> 本文件使用 Go 专用内容扩展了 [common/security.md](../common/security.md)。

## 密钥管理

```go
apiKey := os.Getenv("OPENAI_API_KEY")
if apiKey == "" {
    log.Fatal("OPENAI_API_KEY not configured")
}
```

## 安全扫描

- 使用 **gosec** 进行静态安全分析：
  ```bash
  gosec ./...
  ```

## Context 和 Timeouts

始终使用 `context.Context` 进行超时控制：

```go
ctx, cancel := context.WithTimeout(ctx, 5*time.Second)
defer cancel()
```
