### pyecharts
http://pyecharts.org/#/

### xlrd
https://github.com/python-excel/xlrd


### BarChart

``` python
import xlrd
from pyecharts import Bar

#导入需要读取Excel表格的路径
data = xlrd.open_workbook(r'/home/liang.liang/code/jupyterCode/pydata-book-2nd-edition/examples/demo.xlsx')
table = data.sheets()[1]

#将列的值存入字符串
x=table.col_values(0)#读取列的值
y1=table.col_values(1)#读取列的值

bar = Bar("Bar chart", "Delay Days for Features")
bar.add("Features", x, y1, xaxis_rotate=30,xaxis_interval= 0,mark_line=["average"], mark_point=["max", "min"])

```
