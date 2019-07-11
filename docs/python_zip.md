```python
keys = ['1001', '1002', '1003']
values = ['骆昊', '王大锤', '白元芳']

d_dic = dict(zip(keys, values))
d_list = list(zip(keys, values))
d_tuple = tuple(zip(keys, values))

print(d_dic)   # {'1001': '骆昊', '1002': '王大锤', '1003': '白元芳'}
print(d_list)  # [('1001', '骆昊'), ('1002', '王大锤'), ('1003', '白元芳')]
print(d_tuple) # (('1001', '骆昊'), ('1002', '王大锤'), ('1003', '白元芳'))

```
