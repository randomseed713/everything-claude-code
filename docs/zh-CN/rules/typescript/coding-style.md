# TypeScript/JavaScript 编码风格

> 本文件使用 TypeScript/JavaScript 专用内容扩展了 [common/coding-style.md](../common/coding-style.md)。

## 不可变性

使用扩展运算符进行不可变更新：

```typescript
// 错误：变异
function updateUser(user, name) {
  user.name = name  // 变异！
  return user
}

// 正确：不可变
function updateUser(user, name) {
  return {
    ...user,
    name
  }
}
```

## 错误处理

使用 async/await 配合 try-catch：

```typescript
try {
  const result = await riskyOperation()
  return result
} catch (error) {
  console.error('Operation failed:', error)
  throw new Error('Detailed user-friendly message')
}
```

## 输入验证

使用 Zod 进行基于 schema 的验证：

```typescript
import { z } from 'zod'

const schema = z.object({
  email: z.string().email(),
  age: z.number().int().min(0).max(150)
})

const validated = schema.parse(input)
```

## Console.log

- 生产代码中不要有 `console.log` 语句
- 改用适当的日志库
- 参见 hooks 以了解自动检测
