### 装饰器的使用
它放在一个函数开始定义的地方，它就像一顶帽子一样戴在这个函数的头上,和这个函数绑定在一起。  
装饰器的使用方法很固定：
1. 先定义一个装饰函数（帽子）（也可以用类、偏函数实现）  
2. 再定义你的业务函数、或者类（人） 
3. 最后把这顶帽子带在这个人头上  

### 装饰器的作用
一般装饰器可以用在下类场景中：
- 引入日志
- 计时，用于性能分析
- 给函数增加事务能力


### 举例
```python
def delay(func):
    def wrapper(*args, **kwargs):
        time.sleep(1)
        ret = func(*args, **kwargs)
        print("delay 1 second to call %s" % func.__name__)
        return ret
    return wrapper


@delay
def add(a, b):
    return a + b


if __name__ == "__main__":
    add(1, 2)
```
```log
delay 1 second to call add
```

其中：
- add是被装饰的函数
- delay是装饰器
- wrapper调用被装饰的函数，并作为包装了的函数被返回，注意，Python里面函数就是对象，所以可以被直接返回。
