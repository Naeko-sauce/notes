
```python
class prson:
    def __init__(self, name):
        self.name = name

    def __add__(self, other):
        if isinstance(other, prson):  # 检查是否是 prson 类型的对象
            return "{0}----{1}".format(self.name, other.name)  # 如果是，返回两个对象的连接
        else:
            return "no"  # 如果不是，返回字符串 "no"

    def __mul__(self, other):
        if isinstance(other, int):  # 检查是否是整数类型
            return self.name * other  # 如果是，返回对象的 name 属性重复 other 次的字符串
        else:
            return "no"  # 如果不是，返回字符串 "no"

# 创建两个 prson 对象
p1 = prson("12")
p2 = prson("423")

# 将两个 prson 对象相乘
x = p1 * p2

# 打印结果
print(x)
```

1. `prson` 类有一个构造函数 `__init__`，用于初始化对象并设置 `name` 属性。

2. `__add__` 方法重载了加法运算符 `+`。如果另一个操作数是 `prson` 类型的对象，则返回两个对象的 `name` 属性连接的字符串，以 `"----"` 分隔。如果另一个操作数不是 `prson` 类型的对象，则返回字符串 `"no"`。

3. `__mul__` 方法重载了乘法运算符 `*`。如果另一个操作数是整数类型，则返回该对象的 `name` 属性重复指定次数的字符串。否则，返回字符串 `"no"`。

在代码中，`p1 * p2` 首先调用了 `p1` 的 `__mul__` 方法，并将 `p2` 作为参数传递给 `other`。因为 `p2` 不是整数类型的对象，所以返回 `"no"`。最终打印的结果为 `"no"`。