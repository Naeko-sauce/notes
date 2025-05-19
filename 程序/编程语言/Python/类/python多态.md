多态（polymorphism）是面向对象编程中的一个重要概念，指的是同一个方法调用可以在不同的对象上产生不同的行为。Python 是一种支持多态性的动态类型语言，它允许不同的对象以不同的方式响应相同的方法调用。这种灵活性使得 Python 编程更加简洁和易于理解。

让我们通过一个简单的例子来说明多态的概念：

假设我们有一个基类 Animal，它有一个方法 `make_sound()`，用于表示动物发出声音的行为。然后我们有两个子类 Dog 和 Cat，它们分别重写了 `make_sound()` 方法来表达狗和猫不同的叫声。

```python
class Animal:
    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"
```

现在，我们可以创建 Dog 和 Cat 的实例，并调用它们的 `make_sound()` 方法：

```python
dog = Dog()
cat = Cat()

print(dog.make_sound())  # 输出: Woof!
print(cat.make_sound())  # 输出: Meow!
```

这里，无论是 `dog` 还是 `cat` 对象，我们都可以调用同一个方法 `make_sound()`，但由于它们是不同的类的实例，因此调用结果也是不同的，这就体现了多态性的特征。

多态性使得代码更加灵活和易于扩展。例如，如果我们添加一个新的子类 Mouse，并重写了 `make_sound()` 方法，我们可以很容易地将它与现有的代码集成，而不必修改已有的代码。

```python
class Mouse(Animal):
    def make_sound(self):
        return "Squeak!"

mouse = Mouse()
print(mouse.make_sound())  # 输出: Squeak!
```

这样，我们只需创建一个新的 Mouse 对象，而不必改动之前的代码，就能够实现不同种类动物的声音输出。