### 背景
- 我们常常会需要使用字典来统计序列里面各项出现的次数，key表示序列的项，value表示该项一共出现的次数
- 我们今天来用列表自带的count()和collections.Counter来解决

### count()函数
- 用list的count()方法统计列表中各个元素的个数
- 代码如下
```python
if __name__ == "__main__":
    # 将句子里面的单词抽取成元组
    txt = 'I like python and i use python'
    words = txt.split(' ')
    print(words)

    words_set = set(words)
    counts = dict()
    for word in words_set:
        counts[word] = words.count(word)
    print(counts)
```
```
['I', 'like', 'python', 'and', 'i', 'use', 'python']
{'and': 1, 'use': 1, 'i': 1, 'I': 1, 'python': 2, 'like': 1}
```

### collections.Couter类
- Python的collection包里已经有一个Counter的类，用它一行搞定上面的需求
- Counter类的目的是用来跟踪值出现的次数。它是一个无序的容器类型，以字典的键值对形式存储，其中元素作为key，其计数作为value。计数值可以是任意的Interger（包括0和负数）。
- 代码如下
```python
from collections import Counter

if __name__ == "__main__":
    # 将句子里面的单词抽取成元组
    txt = 'I like python and i use python'
    words = txt.split(' ')
    print(words)

    # 一行代码搞定
    counter = Counter(words)
    print(dict(counter))
```
```
['I', 'like', 'python', 'and', 'i', 'use', 'python']
{'and': 1, 'use': 1, 'i': 1, 'I': 1, 'python': 2, 'like': 1}
```
