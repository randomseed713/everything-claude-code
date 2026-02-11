# Python 安全

> 本文件使用 Python 专用内容扩展了 [common/security.md](../common/security.md)。

## 密钥管理

```python
import os
from dotenv import load_dotenv

load_dotenv()

api_key = os.environ["OPENAI_API_KEY"]  # 如果缺失会抛出 KeyError
```

## 安全扫描

- 使用 **bandit** 进行静态安全分析：
  ```bash
  bandit -r src/
  ```

## 参考

参见 skill：`django-security` 了解 Django 专用安全指南（如适用）。
