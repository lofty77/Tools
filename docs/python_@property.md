@property 使用方法

>@property, 把一个getter方法变成读属性.  
@score.setter，负责把一个setter方法变成写属性.
```python
class Student(object):
    def __init__(self):
        self._score = 0

    @property
    def score(self):
        return self._score

    @score.setter
    def score(self, value):
        if not isinstance(value, int):
            raise ValueError('score must be an integer!')
        if value < 0 or value > 100:
            raise ValueError('score must between 0 ~ 100!')
        self._score = value
```
```python
     s = Student()
     s.score = 100
     s.score  ### 100

```
