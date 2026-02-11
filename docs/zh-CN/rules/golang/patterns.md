# Go 模式

> 本文件使用 Go 专用内容扩展了 [common/patterns.md](../common/patterns.md)。

## Functional Options

```go
type Option func(*Server)

func WithPort(port int) Option {
    return func(s *Server) { s.port = port }
}

func NewServer(opts ...Option) *Server {
    s := &Server{port: 8080}
    for _, opt := range opts {
        opt(s)
    }
    return s
}
```

## 小型 Interfaces

在使用 interfaces 的地方定义它们，而不是在实现它们的地方。

## 依赖注入

使用构造函数注入依赖：

```go
func NewUserService(repo UserRepository, logger Logger) *UserService {
    return &UserService{repo: repo, logger: logger}
}
```

## 参考

参见 skill：`golang-patterns` 了解包括并发、错误处理和包组织在内的全面 Go 模式。
