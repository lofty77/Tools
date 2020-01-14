## 基本技巧

#### 冻结窗口
- [冻结窗口,让表头固定不动](https://baijiahao.baidu.com/s?id=1644350185150069089&wfr=spider&for=pc)

#### 添加批注
- 点击表格-- 右击-- 添加批注
- 如果要让批注一直显示，选择 show comments

#### Excel表格中大于某一数值的显示为一个颜色
- [Excel表格中大于某一数值的显示为一个颜色](https://jingyan.baidu.com/article/a65957f4de46e424e67f9bb7.html)

### setting
- 要开启错误校验
file- option- formuals- enable background error checking ， 勾上
- trim 有副作用，就是强制转格式

### Vlookup
- 一定要加绝对索引! （Vlookup 中的第二个参数）
:joy: 花了3个小时debug这个教训(快捷键 F4)
- 有时候索引列表的id看着一样，其实是不一样的（可以用IF 来判断），这时候可以用TRIM 函数来去除多余的不可见字符

### IF
- 判断两字字符是否相等
- =IF(条件判断, 结果为真返回值, 结果为假返回值)

### TRIM
- 移除空格
- TRIM(text)

### CLEAN
- 移除不可打印字符
- CLEAN(text)

### CODE
- 返回文本字符串中第一个字符的数字代码。 返回的代码对应于本机所使用的字符集.
- CODE(text)
