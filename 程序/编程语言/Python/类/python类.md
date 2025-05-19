在 Python 中，类（Class）是面向对象编程的核心概念之一。类提供了一种创建对象的蓝图或模板，通过类可以定义对象的属性（属性）和行为（方法）。让我们详细地了解 Python 中的类，并举例说明其用法。

### 定义类

使用 `class` 关键字可以定义一个类，类名通常使用大写字母开头的命名规范。

```python
class Person:
    # 类的属性
    species = 'Human'  # 类属性

    # 类的方法
    def __init__(self, name, age):
        self.name = name  # 实例属性
        self.age = age    # 实例属性

    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."
```

在上面的示例中，我们定义了一个名为 `Person` 的类。该类具有类属性 `species`，以及一个初始化方法 `__init__` 和一个实例方法 `greet`。

- `species` 是类属性，它属于类本身，所有实例共享该属性。
- `__init__` 方法是一个特殊的方法，用于初始化对象的状态，也称为构造方法。`self` 表示创建的实例对象本身，用于引用实例属性。
- `greet` 方法是一个实例方法，它定义了对象的行为，可以通过实例对象调用。

### 创建对象（实例化）

通过类可以创建对象，这个过程称为实例化。可以使用类名加括号的方式来创建对象。

```python
# 创建 Person 类的实例对象
person1 = Person('Alice', 30)
person2 = Person('Bob', 25)

# 访问对象的属性和调用方法
print(person1.name)  # 输出: Alice
print(person2.age)   # 输出: 25
print(person1.greet())  # 输出: Hello, my name is Alice and I am 30 years old.
```

在这个示例中，我们创建了两个 `Person` 类的实例对象 `person1` 和 `person2`，并分别访问了它们的属性和调用了方法。

### 类的继承

Python 支持类的继承，一个类可以继承另一个类的属性和方法。

```python
class Student(Person):  # Student 类继承自 Person 类
    def __init__(self, name, age, student_id):
        super().__init__(name, age)  # 调用父类的 __init__ 方法
        self.student_id = student_id  # 新增实例属性

    def study(self, subject):
        return f"{self.name} is studying {subject}."

# 创建 Student 类的实例对象
student1 = Student('Charlie', 20, 'S001')

# 访问继承的属性和调用继承的方法
print(student1.name)       # 输出: Charlie
print(student1.study('Math'))  # 输出: Charlie is studying Math.
```

在这个示例中，`Student` 类继承自 `Person` 类，它继承了 `Person` 类的属性和方法，并添加了自己的 `student_id` 属性和 `study` 方法。

### 封装、继承和多态

面向对象编程的三大特征在 Python 中也得到了支持：

- **封装（Encapsulation）**：使用类来封装数据（属性）和行为（方法），可以通过访问控制符（如私有属性或方法）实现信息隐藏。
- **继承（Inheritance）**：子类可以继承父类的属性和方法，避免重复编写代码。
- **多态（Polymorphism）**：不同类的对象可以对同一消息做出响应，实现了方法的多态性。

### 总结

通过定义类和创建对象，我们可以在 Python 中使用面向对象的方式来组织和管理代码，提高代码的复用性和可维护性。类的概念是理解 Python 面向对象编程的关键，可以通过类来模拟现实世界中的各种对象和关系。