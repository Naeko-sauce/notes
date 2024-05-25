理解了，你想了解一些 Python 对象中常见的特殊属性。除了 `__dict__` 之外，还有一些其他常见的特殊属性，例如：

1. `__class__`: 对象所属的类。

```python
class MyClass:
    pass

obj = MyClass()
print(obj.__class__)  # 输出: <class '__main__.MyClass'>
```

2. `__module__`: 对象所属的模块名称。

```python
import math

print(math.__module__)  # 输出: math
```

3. `__name__`: 如果对象是一个模块，则为模块的名称。

```python
import math

print(math.__name__)  # 输出: math
```

4. `__doc__`: 对象的文档字符串，用于存储对象的说明文档。

```python
class MyClass:
    """This is a sample class."""
    pass

obj = MyClass()
print(obj.__doc__)  # 输出: This is a sample class.
```

5. `__bases__`: 对象的基类元组。

```python
class BaseClass:
    pass

class SubClass(BaseClass):
    pass

obj = SubClass()
print(obj.__bases__)  # 输出: (<class '__main__.BaseClass'>,)
```

6. `__slots__`: 限制对象动态添加属性的列表。

```python
class MyClass:
    __slots__ = ['name', 'age']

obj = MyClass()
obj.name = 'Alice'
obj.age = 30
obj.address = '123 Street'  # 会报错，因为 'address' 不在 __slots__ 中
```

这些特殊属性提供了关于 Python 对象的一些元信息，可以帮助你了解对象的结构和属性。