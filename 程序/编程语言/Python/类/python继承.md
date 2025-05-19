在 Python 中，继承是一种面向对象编程的重要概念，允许一个类（称为子类或派生类）从另一个类（称为父类或基类）中继承属性和方法。子类可以继承父类的所有属性和方法，并且可以在需要时扩展或修改它们。

下面是一个简单的示例，说明如何在 Python 中使用继承：

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def sound(self):
        pass  # 抽象方法，由子类实现


class Dog(Animal):
    def sound(self):
        return "Woof!"


class Cat(Animal):
    def sound(self):
        return "Meow!"


# 创建实例并调用方法
dog = Dog("Buddy")
print(dog.name)  # 输出: Buddy
print(dog.sound())  # 输出: Woof!

cat = Cat("Whiskers")
print(cat.name)  # 输出: Whiskers
print(cat.sound())  # 输出: Meow!
```

在这个示例中，我们定义了一个基类 `Animal`，它有一个 `__init__` 方法用于初始化动物的名称，并且有一个抽象方法 `sound`，在基类中它没有具体的实现。然后，我们定义了两个子类 `Dog` 和 `Cat`，它们分别继承了基类 `Animal`。每个子类都提供了 `sound` 方法的具体实现，分别返回狗的叫声 "Woof!" 和猫的叫声 "Meow!"。

通过这样的继承关系，子类可以访问并重用父类的属性和方法，同时可以根据需要对其进行扩展或修改。这种方式提高了代码的重用性和可维护性，并且使得面向对象编程更加灵活。