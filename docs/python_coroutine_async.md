## 协程-异步IO

### asyncio (Python 3.4)
asyncio是Python 3.4版本引入的标准库，直接内置了对异步IO的支持
```python
import time
import asyncio

@asyncio.coroutine
def hello():
    print('Hello world!')
    yield from asyncio.sleep(1)
    print('Hello end!')
tasks = [hello(), hello()]

loop = asyncio.get_event_loop()
loop.run_until_complete(asyncio.wait(tasks))
loop.close()
```
两个hello()是由同一个线程并发执行的,返回结果为
```log
# 单线程依次执行print('Hello world!')
Hello world!
Hello world!
# 执行异步操作asyncio.sleep(1)
暂停1s
# 单线程依次执行print('Hello end!')
Hello end!
Hello end!
```


