### 一般形式
- reduce()函数接受两个参数，形如reduce(func, seq)
- 第一个参数func是一个函数（有两个参数）
- 第二个参数seq是一个序列/元组
- func先对seq中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 func 函数运算，依此反复，直到seq中所有的元素被遍历完
- 最终结果被reduce()返回


### 例子
- reduce()特别适合进行累计求值
- 下面的例子演示如何使用reduce()进行求和和求积
```
# 计算和
sum_result = reduce(lambda x, y: x+y, range(1, 10))
assert(sum_result == 45)
print(sum_result)

# 计算阶乘
factorial_result = reduce(lambda x, y: x * y, range(1, 10))
assert(factorial_result == 362880)
print(factorial_result)
```
