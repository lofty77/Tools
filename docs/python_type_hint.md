### Reference
[link](https://docs.python.org/3.5/library/typing.html?highlight=type%20hint#module-typing)

### Union
Union[X, Y] means either X or Y.  
To define a union, use e.g. Union[int, str]. Details:  
The arguments must be types and there must be at least one.  

- The arguments must be types and there must be at least one.
- Unions of unions are flattened, e.g.:
```python
Union[Union[int, str], float] == Union[int, str, float]
```

- Unions of a single argument vanish, e.g.:
```python
Union[int] == int  # The constructor actually returns int
```

- Redundant arguments are skipped, e.g.:
```python
Union[int, str, int] == Union[int, str]
```

- When comparing unions, the argument order is ignored, e.g.:
```python
Union[int, str] == Union[str, int]
```

- When a class and its subclass are present, the latter is skipped, e.g.:
``` python
Union[int, object] == object
```

- You cannot subclass or instantiate a union.
- You cannot write Union[X][Y].
- You can use Optional[X] as a shorthand for Union[X, None].




### Optional
Optional type.

- Optional[X] is equivalent to Union[X, None].

Note that this is not the same concept as an optional argument, 
which is one that has a default. An optional argument with a default 
needn’t use the Optional qualifier on its type annotation 
(although it is inferred if the default is None). 
A mandatory argument may still have an Optional type if an explicit value of None is allowed.
