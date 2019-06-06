### 作用
- Python中filter()函数能够通过函数过滤序列
- 最终返回一个新的列表

### 形式
- filter()函数接受两个参数，形如filter(func, seq)
- 第一个参数func是一个函数
- 第二个参数seq是一个序列
- filter()将调用函数func，参数是序列seq的每一个元素上
- 如果func对某元素的返回值为真，则将该元素加入到新列表中
- 最终返回这个新列表


### 例子
下面的例子演示了如何过滤成人年龄
```python
adult_ages = filter(lambda x: x >= 18, range(1, 30))
print(list(adult_ages))
```
`[19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29]`
