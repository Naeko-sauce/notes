## Python 中的私有变量和私有方法

  

在Python中，我们可以通过使用双下划线前缀进行声明（例如 `__var`），从而将类的变量或方法设置为私有。私有变量或方法只能在类的内部被访问，无法从类的外部进行访问。这一特性使得我们可以更好地保护数据，防止数据被意外修改。

  

下面是一个简单的例子：我们创建一个叫做 `Car` 的类，该类中包含一个私有变量 `__speed` 和一个私有方法 `__accelerate`。

  

python

``` python
class Car: 
    def __init__(self):
        self.__speed = 0  # 私有变量, 表示汽车的速度

    def __accelerate(self, amount):  # 私有方法, 用于增加汽车的速度
        self.__speed += amount

    def drive(self, amount):  # 公有方法, 可以在类的外部被调用，通过这个方法间接调用私有方法
        self.__accelerate(amount)
        return self.__speed

my_car = Car()
print(my_car.drive(50))  # 输出: 50
```

  

在上面的代码中，`__speed` 是一个私有变量，`__accelerate` 是一个私有方法。我们不能够直接在类的外部访问这些私有变量或方法，例如尝试 `my_car.__speed` 或者 `my_car.__accelerate(50)` 都将会导致错误。

  

然而，我们可以通过公有方法 `drive()` 来间接调用私有方法和访问私有变量：

  

python

``` python
print(my_car.drive(50))  # 输出: 50
```

  

这种方式使我们能够在类的外部对私有方法进行调用并访问私有变量，同时也保证了数据的安全性。

  

关于此主题，你可以参阅这个[Wikipedia链接](https://zh.wikipedia.org/wiki/%E5%B0%81%E8%A3%9D_%28%E7%89%A9%E4%BB%B6%E5%B0%8E%E5%90%91%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%29)，其中包含了更多关于封装以及其他对象导向知识的详细信息。