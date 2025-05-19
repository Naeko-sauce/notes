在 Python 中，`@property` 装饰器用于将类的方法转换为只读属性。它允许你使用面向对象编程风格，将类的私有属性暴露为公共属性，但同时可以控制对该属性的访问。通过使用 `@property`，你可以定义一个方法来获取属性值，并且可以选择性地定义另一个方法来设置属性值。

### @property 的作用
1. **封装属性**：可以将内部属性（通常以 `_` 开头的私有属性）暴露为公共属性，并通过方法控制其访问。
2. **数据验证**：可以在设置属性值时添加验证逻辑，确保属性值符合预期。
3. **只读属性**：可以创建只读属性，使得属性只能被读取而不能被修改。
4. **懒加载**：可以在第一次访问属性时计算属性值，并缓存结果以供后续访问。

### 使用 @property 的基本示例

下面是一个基本示例，展示如何使用 `@property` 装饰器：

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value

    @property
    def diameter(self):
        return self._radius * 2

    @property
    def area(self):
        import math
        return math.pi * (self._radius ** 2)

# 创建一个 Circle 对象
c = Circle(5)

# 访问属性
print(c.radius)  # 输出: 5
print(c.diameter)  # 输出: 10
print(c.area)  # 输出: 78.53981633974483

# 设置属性
c.radius = 10
print(c.radius)  # 输出: 10
print(c.diameter)  # 输出: 20
print(c.area)  # 输出: 314.1592653589793

# 尝试设置负值，会引发 ValueError
try:
    c.radius = -5
except ValueError as e:
    print(e)  # 输出: Radius cannot be negative
```

### 详细解释

- **初始化方法 (`__init__`)**：我们在初始化方法中定义了一个私有属性 `_radius`。
- **获取器方法 (`@property`)**：使用 `@property` 装饰器定义了 `radius` 方法，使得 `radius` 成为一个属性，访问 `c.radius` 时会调用这个方法。
- **设置器方法 (`@radius.setter`)**：使用 `@radius.setter` 装饰器定义了 `radius` 的设置器方法，允许我们通过 `c.radius = value` 来设置 `radius` 的值，并在设置时进行验证。
- **只读属性 (`diameter` 和 `area`)**：使用 `@property` 装饰器定义了只读属性 `diameter` 和 `area`，它们只能通过计算获得，不能被直接修改。

### 进阶示例

有时你可能只需要一个只读属性，而不需要设置器。下面是一个只读属性的示例：

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @property
    def fahrenheit(self):
        return (self._celsius * 9/5) + 32

# 创建一个 Temperature 对象
t = Temperature(25)

# 访问只读属性
print(t.celsius)  # 输出: 25
print(t.fahrenheit)  # 输出: 77.0

# 尝试设置只读属性（会失败）
try:
    t.fahrenheit = 100
except AttributeError as e:
    print(e)  # 输出: can't set attribute
```

在这个示例中，`fahrenheit` 属性是一个只读属性，因为我们没有为其定义设置器方法。这意味着我们只能读取 `fahrenheit` 的值，而不能直接设置它。