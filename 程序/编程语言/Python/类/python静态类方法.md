在 Python 中，类方法和静态方法是两种不同类型的方法，它们可以在类的内部定义并被调用，但有不同的使用方式和行为。

### 类方法（Class Method）

类方法是定义在类中的方法，它使用装饰器 `@classmethod` 来标识。类方法的第一个参数通常被命名为 `cls`，表示该类本身。通过这个参数，类方法可以访问和修改类级别的属性，而不是实例级别的属性。

**语法：**
```python
class MyClass:
    @classmethod
    def class_method(cls, arg1, arg2, ...):
        # 在类方法中可以访问类属性，而不需要实例化对象
        cls.attribute  # 访问类属性
        cls.method()   # 调用类方法
```

**示例：**
```python
class Car:
    number_of_cars = 0  # 类属性

    def __init__(self, make, model):
        self.make = make
        self.model = model
        Car.number_of_cars += 1

    @classmethod
    def display_number_of_cars(cls):
        print(f"Number of cars created: {cls.number_of_cars}")

# 使用类方法
Car.display_number_of_cars()  # 输出: Number of cars created: 0

car1 = Car("Toyota", "Corolla")
Car.display_number_of_cars()  # 输出: Number of cars created: 1

car2 = Car("Honda", "Civic")
Car.display_number_of_cars()  # 输出: Number of cars created: 2
```

在上面的示例中，`display_number_of_cars` 是一个类方法，它通过 `cls.number_of_cars` 来访问并显示了已创建的汽车数量，而不需要实例化任何对象。

### 静态方法（Static Method）

静态方法与类方法不同，它使用装饰器 `@staticmethod` 来标识。静态方法既不能访问类属性，也不能访问实例属性，它与类本身关联，但是不能访问类或实例的状态。

**语法：**
```python
class MyClass:
    @staticmethod
    def static_method(arg1, arg2, ...):
        # 在静态方法中无法访问类属性或实例属性
        # 只能进行一些独立的操作
```

**示例：**
```python
class MathOperations:
    @staticmethod
    def add(x, y):
        return x + y
    
    @staticmethod
    def multiply(x, y):
        return x * y

# 使用静态方法
print(MathOperations.add(5, 3))       # 输出: 8
print(MathOperations.multiply(5, 3))  # 输出: 15
```

在上面的示例中，`add` 和 `multiply` 是静态方法，它们在类中定义，但不依赖于任何类属性或实例属性。这些方法可以直接通过类名调用，而不需要创建类的实例。

### 区别总结

- 类方法可以访问和修改类属性，可以通过类名或实例调用，第一个参数是 `cls` 表示类本身。
- 静态方法不能访问类属性或实例属性，它们与类相关联但独立于类的状态，通过类名调用。

在选择使用类方法还是静态方法时，取决于方法是否需要访问或修改类属性或实例属性。