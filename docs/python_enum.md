Python 枚举类处理方式

```python
from enum import Enum, unique

@unique
class Color(Enum):
    red = "red_detail"
    blue = "blue_detail"

red_member = Color.red

print("name: "+red_member.name)
print("value: "+red_member.value)
# name: red
# value: red_detail
```
