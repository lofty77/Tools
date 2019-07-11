```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]

for key,value in enumerate(seasons):
    print("key:{0},value:{1}".format(key,value))

# key:0,value:Spring
# key:1,value:Summer
# key:2,value:Fall
# key:3,value:Winter
```
