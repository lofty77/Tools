### 生成器语法
- Python中的生成器是一个带yield语句的函数
- 生成器运行到yield，会通过yield返回一个中间值给调用者，并且暂停执行
- 当生成器的next()被调用的时候，它会从上次离开的地方继续执行，一直执行到yield 为止
- Python的for循环自带next()调用和对StopIteration的处理，常常用来迭代一个生成器

### 最佳用途
- 使用生成器最好的地方就是迭代一个巨大的数据集合时对每个元素进行及时的操作和处理（节约内存，提升速度）

### 生成器的原理
- 生成斐波那契數列
```python
class Fab(object): 
 
    def __init__(self, max): 
        self.max = max 
        self.n, self.a, self.b = 0, 0, 1 
 
    def __iter__(self): 
        return self 
 
    def __next__(self): 
        if self.n < self.max: 
            r = self.b 
            self.a, self.b = self.b, self.a + self.b 
            self.n = self.n + 1 
            return r 
        raise StopIteration()

for n in Fab(5): 
    print(n)
#1
#1
#2
#3
#5
```

### 生成器实例
- 生成斐波那契數列
```python
def fab(max): 
    n, a, b = 0, 0, 1 
    while n < max: 
        yield b      
        a, b = b, a + b 
        n = n + 1
 
for n in fab(5): 
    print (n)

#1
#1
#2
#3
#5
```
