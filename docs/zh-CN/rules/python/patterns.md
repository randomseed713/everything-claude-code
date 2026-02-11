# Python 模式

> 本文件使用 Python 专用内容扩展了 [common/patterns.md](../common/patterns.md)。

## Protocol（鸭子类型）

```python
from typing import Protocol

class Repository(Protocol):
    def find_by_id(self, id: str) -> dict | None: ...
    def save(self, entity: dict) -> dict: ...
```

## Dataclasses 作为 DTOs

```python
from dataclasses import dataclass

@dataclass
class CreateUserRequest:
    name: str
    email: str
    age: int | None = None
```

## Context Managers 和 Generators

- 使用 context managers（`with` 语句）进行资源管理
- 使用 generators 实现惰性求值和内存高效的迭代

## 参考

参见 skill：`python-patterns` 了解包括装饰器、并发和包组织在内的全面模式。
