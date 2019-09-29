# Python-装饰器

装饰器在不修改源代码块的情况下,增加代码的功能,有助于代码的精简,抽象出公共的辅助模块,便于维护代码

* [Python之禅-理解 Python 装饰器看这一篇就够了][1]
* [廖雪峰-装饰器][2]
* [Python进阶-装饰器][3]

## 入门

**入门主要以python之禅的教程**,谈装饰器前，还要先要明白一件事，Python 中的函数和 Java、C++不太一样，Python 中的函数可以像普通变量一样当做参数传递给另外一个函数

```py
def foo():
    print("foo")

def bar(func):
    func()

bar(foo)
```

装饰器本质上是一个 Python **函数或类**，它可以让其他函数或类在不需要做任何代码修改的前提下增加额外功能，装饰器的返回值也是一个函数/类对象。它经常用于**有切面需求的场景**，比如：插入日志、性能测试、事务处理、缓存、权限校验等场景，装饰器是解决这类问题的绝佳设计。有了装饰器，我们就可以抽离出大量与函数功能本身无关的雷同代码到装饰器中并继续重用。概括的讲，装饰器的作用就是为已经存在的对象添加额外的功能

```py
# 打印日志为例子
def use_logging(func):
    logging.warn("%s is running" % func.__name__)
    func()

def foo():
    print('i am foo')
# 打印日志的功能可以实现 但是破坏了原来的代码结构 变成每次调用foo都要调用 use_logging(foo)
use_logging(foo)
```

```py
def use_logging(func):

    def wrapper():
        logging.warn("%s is running" % func.__name__)
        return func()   # 把 foo 当做参数传递进来时，执行func()就相当于执行foo()
    return wrapper

def foo():
    print('i am foo')

foo = use_logging(foo)  # 因为装饰器 use_logging(foo) 返回的时函数对象 wrapper，这条语句相当于  foo = wrapper
foo()
```

use_logging 就是一个装饰器，它一个普通的函数，它把执行真正业务逻辑的函数 func 包裹在其中，看起来像 foo 被 use_logging 装饰了一样，use_logging 返回的也是一个函数，这个函数的名字叫 wrapper。在这个例子中，函数进入和退出时，被称为一个横切面，这种编程方式被称为**面向切面的编程**

### @语法糖

此时会发现还是要为程序多添加一句`foo = use_logging(foo)`,python提供了`@`的语法糖,用于省略`foo = use_logging(foo)`这样的赋值功能

```py
def use_logging(func):
    def wrapper():
        logging.warn("%s is running" % func.__name__)
        return func()
    return wrapper
@use_logging  # 实现了 foo = use_logging(foo) 的功能
def foo():
    print('i am foo')
foo()
```

### 装饰有参数的函数

```py
# 相当于 foo = use_logging(foo) 返回的是一个 wrapper 函数, 然后调用 wrapper(name, age=None, height=None)
def use_logging(func):
    def wrapper(*args, **kwargs):
        # args是一个数组，kwargs一个字典
        logging.warn("%s is running" % func.__name__)
        return func(*args, **kwargs)
    return wrapper
@use_logging
def foo(name, age=None, height=None):
    print("I am %s, age %s, height %s" % (name, age, height))
```

### 带参数的装饰器

装饰器还有更大的灵活性，例如带参数的装饰器。装饰器的语法允许我们在调用时，提供其它参数，比如@decorator(a)。这样，就为装饰器的编写和使用提供了更大的灵活性。比如，我们可以在装饰器中指定日志的等级，因为不同业务函数可能需要的日志级别是不一样的

```py
def use_logging(level):
    def decorator(func):
        def wrapper(*args, **kwargs):
            if level == "warn":
                logging.warn("%s is running" % func.__name__)
            elif level == "info":
                logging.info("%s is running" % func.__name__)
            return func(*args)
        return wrapper
    return decorator
@use_logging(level="warn")
def foo(name='foo'):
    print("i am %s" % name)
foo()
```

### 类装饰器

相比函数装饰器，类装饰器具有灵活度大、高内聚、封装性 可继承性(详见[Python进阶-装饰器][3])等优点。使用类装饰器主要依靠类的`__call__`方法，当使用 @ 形式将装饰器附加到函数上时，就会调用此方法。

```py
class Foo(object):
    def __init__(self, func):
        self._func = func

    def __call__(self):
        print ('class decorator runing')
        self._func()
        print ('class decorator ending')
@Foo
def bar():
    print ('bar')
bar()
```

### functools.wraps 找回被装饰函数的元信息

```py
from functools import wraps
def logged(func):
    @wraps(func)  # with_logging = wraps(with_logging)
    def with_logging(*args, **kwargs):
        print func.__name__      # 输出 'f',如果没有@wraps(func)返回的是with_logging
        print func.__doc__       # 输出 'does some math',如果没有@wraps(func)返回的是None
        return func(*args, **kwargs)
    return with_logging
@logged
def f(x):
   """does some math"""
   return x + x * x
# 这个相当于 f = wraps(logged(f))
```

### 多个装饰器

```py
@a
@b
@c
def f ():
    pass
```

执行顺序是从里到外，最先调用最里层的装饰器，最后调用最外层的装饰器，它等效于`f = a(b(c(f)))`

---

[1]: https://foofish.net/python-decorator.html
[2]: https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386819879946007bbf6ad052463ab18034f0254bf355000
[3]: https://eastlakeside.gitbooks.io/interpy-zh/content/decorators/
