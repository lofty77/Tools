```python
import objgraph

if __name__ == "__main__":
    x = [1,2]
    y = [x,[x],dict(x=x)]
    objgraph.show_refs([y], filename='/home/liang.liang/code/test/sample-graph.png')
```

![sample-graph](https://github.com/lofty77/Tools/blob/master/attached/python_objgraph_sample-graph.png)
