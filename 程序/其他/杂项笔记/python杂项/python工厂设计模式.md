工厂模式（Factory Pattern）是一种创建型设计模式，它定义了一个接口用于创建对象，但让子类决定实例化哪一个类。工厂模式使一个类的实例化延迟到其子类。工厂模式可以分为简单工厂模式、工厂方法模式和抽象工厂模式。

### 简单工厂模式

简单工厂模式不属于 23 种设计模式，但通常是工厂方法模式的一个特殊实现。它通过一个单独的类来创建不同类的实例，根据传递的参数来决定创建哪种实例。

#### 示例

假设我们有一个用于创建不同类型水果对象的简单工厂。

```python
class Apple:
    def get_name(self):
        return "Apple"

class Banana:
    def get_name(self):
        return "Banana"

class FruitFactory:
    @staticmethod
    def create_fruit(fruit_type):
        if fruit_type == "Apple":
            return Apple()
        elif fruit_type == "Banana":
            return Banana()
        else:
            raise ValueError("Unknown fruit type")

# 使用简单工厂
fruit = FruitFactory.create_fruit("Apple")
print(fruit.get_name())  # 输出: Apple

fruit = FruitFactory.create_fruit("Banana")
print(fruit.get_name())  # 输出: Banana
```

### 工厂方法模式

工厂方法模式使用子类来决定实例化的类。它通过定义一个创建对象的接口，但由子类决定具体实例化的类来实现。

#### 示例

我们扩展上面的例子，使用工厂方法模式来创建不同的水果。

```python
from abc import ABC, abstractmethod

# 抽象产品
class Fruit(ABC):
    @abstractmethod
    def get_name(self):
        pass

# 具体产品
class Apple(Fruit):
    def get_name(self):
        return "Apple"

class Banana(Fruit):
    def get_name(self):
        return "Banana"

# 抽象工厂
class FruitFactory(ABC):
    @abstractmethod
    def create_fruit(self):
        pass

# 具体工厂
class AppleFactory(FruitFactory):
    def create_fruit(self):
        return Apple()

class BananaFactory(FruitFactory):
    def create_fruit(self):
        return Banana()

# 使用工厂方法
apple_factory = AppleFactory()
apple = apple_factory.create_fruit()
print(apple.get_name())  # 输出: Apple

banana_factory = BananaFactory()
banana = banana_factory.create_fruit()
print(banana.get_name())  # 输出: Banana
```

### 抽象工厂模式

抽象工厂模式提供一个创建一系列相关或依赖对象的接口，而无需指定它们具体的类。

#### 示例

假设我们有两个系列的水果：普通水果和热带水果，每个系列有不同的水果。

```python
from abc import ABC, abstractmethod

# 抽象产品
class Fruit(ABC):
    @abstractmethod
    def get_name(self):
        pass

# 具体产品
class Apple(Fruit):
    def get_name(self):
        return "Apple"

class Banana(Fruit):
    def get_name(self):
        return "Banana"

class Mango(Fruit):
    def get_name(self):
        return "Mango"

class Pineapple(Fruit):
    def get_name(self):
        return "Pineapple"

# 抽象工厂
class FruitFactory(ABC):
    @abstractmethod
    def create_apple(self):
        pass

    @abstractmethod
    def create_banana(self):
        pass

    @abstractmethod
    def create_tropical(self):
        pass

# 具体工厂
class RegularFruitFactory(FruitFactory):
    def create_apple(self):
        return Apple()

    def create_banana(self):
        return Banana()

    def create_tropical(self):
        return None

class TropicalFruitFactory(FruitFactory):
    def create_apple(self):
        return None

    def create_banana(self):
        return Banana()

    def create_tropical(self):
        return Mango()

# 使用抽象工厂
regular_factory = RegularFruitFactory()
apple = regular_factory.create_apple()
print(apple.get_name())  # 输出: Apple

tropical_factory = TropicalFruitFactory()
tropical = tropical_factory.create_tropical()
print(tropical.get_name())  # 输出: Mango
```

通过这些示例，你可以看到工厂模式在对象创建过程中的强大和灵活性。工厂模式通过封装实例化逻辑，使得代码更加灵活、可扩展和易于维护。