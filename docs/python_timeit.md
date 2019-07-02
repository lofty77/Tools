## 官方
- [timeit](https://docs.python.org/zh-cn/3/library/timeit.html)

## 基本用法（有参数）

```python
import time
def f(x):
    time.sleep(int(x))

import timeit
print(timeit.timeit('f(1)', number=2,globals=globals()))
#2.003052280997508
```
