### 装饰器的使用
它放在一个函数开始定义的地方，它就像一顶帽子一样戴在这个函数的头上,和这个函数绑定在一起。  
在我们调用这个函数的时候，第一件事并不是执行这个函数，而是将这个函数做为参数传入它头顶上这顶帽子，这顶帽子我们称之为装饰函数或装饰器.  

装饰器的使用方法很固定：
先定义一个装饰函数（帽子）（也可以用类、偏函数实现）  
再定义你的业务函数、或者类（人） 
最后把这顶帽子带在这个人头上  

装饰器的简单的用法有很多，这里举两个常见的。
日志打印器
时间计时器

### 装饰器的作用
装饰器用来装饰函数，可以在被装饰的函数调用前做些准备工作，在被装饰的函数调用后做些清理工作，这样的特征使它在AOP（Aspect Oriented Programming面向切面编程）方面被广泛利用。
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
