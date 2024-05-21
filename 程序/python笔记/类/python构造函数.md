在 Python 编程中，构造函数用于初始化对象。构造函数在定义类时使用特殊方法 `__init__` 来实现。每当创建类的实例时，`__init__` 方法会自动调用，并初始化对象的属性。下面详细介绍 Python 中的构造函数并举例说明。

### 构造函数的特性

1. **使用 `__init__` 方法**：构造函数在类中定义为 `__init__(self, ...)`。
2. **自动调用**：创建类实例时，`__init__` 方法自动调用。
3. **初始化对象**：用于设置对象的初始状态。
4. **参数可选**：可以定义带参数或不带参数的构造函数。

### 示例代码

```python
# 定义一个名为Person的类
class Person:
    # 构造函数
    def __init__(self, name="Unknown", age=0):
        self.name = name
        self.age = age

    # 定义一个方法来显示信息
    def display_info(self):
        print(f"Name: {self.name}, Age: {self.age}")

# 创建Person类的实例，不传递任何参数
person1 = Person()
person1.display_info()  # 输出：Name: Unknown, Age: 0

# 创建Person类的实例，传递name和age参数
person2 = Person("Alice", 30)
person2.display_info()  # 输出：Name: Alice, Age: 30

# 创建Person类的实例，只传递name参数
person3 = Person(name="Bob")
person3.display_info()  # 输出：Name: Bob, Age: 0

# 创建Person类的实例，只传递age参数
person4 = Person(age=25)
person4.display_info()  # 输出：Name: Unknown, Age: 25
```

### 详细说明

1. **定义构造函数**：
    ```python
    def __init__(self, name="Unknown", age=0):
        self.name = name
        self.age = age
    ```
    - `__init__` 方法是构造函数，它的第一个参数必须是 `self`，表示实例本身。
    - 可以通过在参数列表中设置默认值来实现无参数构造和带参数构造的灵活性。
    - `self.name` 和 `self.age` 是实例变量，用于存储每个实例的状态。

2. **创建实例**：
    - `person1 = Person()`：
        - 创建 `Person` 对象，不传递任何参数，使用默认值 `name="Unknown"` 和 `age=0`。
    - `person2 = Person("Alice", 30)`：
        - 创建 `Person` 对象，传递 `name="Alice"` 和 `age=30`，覆盖默认值。
    - `person3 = Person(name="Bob")`：
        - 创建 `Person` 对象，只传递 `name="Bob"`，`age` 使用默认值0。
    - `person4 = Person(age=25)`：
        - 创建 `Person` 对象，只传递 `age=25`，`name` 使用默认值"Unknown"。

3. **显示信息的方法**：
    ```python
    def display_info(self):
        print(f"Name: {self.name}, Age: {self.age}")
    ```
    - 这是一个普通的方法，用于打印实例的 `name` 和 `age` 属性。

通过这些示例，可以看到 Python 中的构造函数如何用于初始化对象的状态，并通过参数实现初始化的灵活性。构造函数在对象创建时自动调用，为每个对象设置初始值，使得每个实例具有独立的状态。