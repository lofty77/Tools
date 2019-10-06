## 问题
Sublime 下报错 ：ModuleNotFoundError: No module named 'pymysql

## 解决办法

``` python
import sys
print(sys.executable)
print(sys.path)
```
```python
/usr/local/bin/python3
['/Users/lc/code/test', '/Library/Frameworks/Python.framework/Versions/3.7/lib/python37.zip',
  '/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7',
 '/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/lib-dynload',
  '/Users/lc/Library/Python/3.7/lib/python/site-packages',
'/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/site-packages']  
```



### 查看 pymysql 安装路径

```python
pip show pymysql
```
```python
(base) LCdeMacBook-Air:pymysql lc$ pip show pymysql
Name: PyMySQL
Version: 0.9.3
Summary: Pure Python MySQL Driver
Home-page: https://github.com/PyMySQL/PyMySQL/
Author: yutaka.matsubara
Author-email: yutaka.matsubara@gmail.com
License: "MIT"
Location: /anaconda3/lib/python3.7/site-packages
Requires: 
Required-by: 
```
**Location: /anaconda3/lib/python3.7/site-packages**

## 结论
**location 不在sys.path 中**

## 解决
cp 　-r 　/anaconda3/lib/python3.7/site-packages/pymysql　　/Users/lc/Library/Python/3.7/lib/python/site-packages/
