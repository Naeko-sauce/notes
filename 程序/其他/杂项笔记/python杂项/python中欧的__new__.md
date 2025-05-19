
在 Python 中，`__new__` 是一个特殊方法，用于创建类的实例。与 `__init__` 不同，`__new__` 是在实例创建之前被调用的，用于控制实例的创建过程。`__new__` 方法是一个类方法（静态方法），它接收类作为第一个参数，并返回一个新实例。 

### `__new__` 方法的详细解释

- `__new__` 是一个静态方法，由类调用，而不是由实例调用。
- `__new__` 方法用于创建并返回一个新实例。它是实例创建的真正负责者。
- `__new__` 方法的签名通常是 `__new__(cls, *args, **kwargs)`，其中 `cls` 是当前类。

### `__new__` 与 `__init__` 的区别

- `__new__` 创建并返回一个实例。
- `__init__` 初始化实例属性。
- `__new__` 方法在实例创建之前调用，而 `__init__` 方法在实例创建之后调用。

### 示例：`__new__` 的使用

下面是一个使用 `__new__` 方法的示例，用于实现一个不可变的（immutable）点（Point）类：

```python
class Point:
    def __new__(cls, x, y):
        instance = super().__new__(cls)
        instance._initialized = False
        return instance

    def __init__(self, x, y):
        if not self._initialized:
            self.x = x
            self.y = y
            self._initialized = True

    def __setattr__(self, name, value):
        if self._initialized:
            raise AttributeError("Cannot modify an immutable instance")
        super().__setattr__(name, value)

    def __repr__(self):
        return f"Point({self.x}, {self.y})"

# 使用示例
p1 = Point(2, 3)
print(p1)  # 输出: Point(2, 3)

# 尝试修改属性
try:
    p1.x = 5
except AttributeError as e:
    print(e)  # 输出: Cannot modify an immutable instance
```

### 详细解释

1. **`__new__` 方法**：
   ```python
   def __new__(cls, x, y):
       instance = super().__new__(cls)
       instance._initialized = False
       return instance
   ```
   - 调用 `super().__new__(cls)` 创建一个新的实例。
   - 设置 `instance._initialized` 为 `False` 以标记实例尚未初始化。
   - 返回创建的实例。

2. **`__init__` 方法**：
   ```python
   def __init__(self, x, y):
       if not self._initialized:
           self.x = x
           self.y = y
           self._initialized = True
   ```
   - 检查 `_initialized` 是否为 `False`，只有在实例尚未初始化时才执行初始化操作。
   - 设置实例属性 `x` 和 `y`，并将 `_initialized` 设置为 `True`，防止再次初始化。

3. **`__setattr__` 方法**：
   ```python
   def __setattr__(self, name, value):
       if self._initialized:
           raise AttributeError("Cannot modify an immutable instance")
       super().__setattr__(name, value)
   ```
   - 重载 `__setattr__` 方法，检查 `_initialized` 是否为 `True`，如果是，则禁止修改属性，抛出 `AttributeError`。
   - 否则，使用 `super().__setattr__(name, value)` 设置属性。

4. **`__repr__` 方法**：
   ```python
   def __repr__(self):
       return f"Point({self.x}, {self.y})"
   ```
   - 提供实例的字符串表示形式。

### 单例模式中的 `__new__`

在单例模式中，`__new__` 方法也起到关键作用，确保类只有一个实例。以下是单例模式的例子：

```python
class Singleton:
    _instance = None

    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

    def __init__(self, value):
        if not hasattr(self, '_initialized'):
            self.value = value
            self._initialized = True

# 测试单例模式
singleton1 = Singleton("first")
singleton2 = Singleton("second")

print(singleton1 is singleton2)  # 输出: True
print(singleton1.value)  # 输出: first
print(singleton2.value)  # 输出: first
```

在这个示例中：

- `__new__` 方法确保只有一个实例 `cls._instance`。
- `__init__` 方法通过 `self._initialized` 防止重复初始化。

通过以上解释和示例，可以清楚地理解 `__new__` 方法在 Python 中的作用及其与 `__init__` 方法的区别和配合。