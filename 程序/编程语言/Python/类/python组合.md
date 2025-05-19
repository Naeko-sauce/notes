在 Python 中，组合是一种设计模式，用于创建一个包含其他对象的新对象。通过组合，一个类可以将其他类的实例作为自己的属性，从而实现代码的重用和模块化。以下是一个详细的说明和示例：

### 详细说明：

1. **定义**：
   - 组合是一种设计模式，其中一个类包含另一个类的一个或多个实例作为其属性。
   - 通过组合，一个类可以利用其他类的功能，实现更复杂的行为。

2. **实现方式**：
   - 在类的构造函数中创建其他类的实例，并将其赋值给该类的属性。

3. **优点**：
   - 提高了代码的重用性和模块化程度。
   - 可以更灵活地扩展功能。

4. **示例场景**：
   - 一个汽车类可以包含一个引擎类的实例作为其属性，实现汽车的驱动功能。
   - 一个电脑类可以包含一个 CPU 类和一个内存类的实例作为其属性，实现电脑的运算和存储功能。

### 示例代码：

```python
class Engine:
    def start(self):
        print("Engine started")

    def stop(self):
        print("Engine stopped")

class Car:
    def __init__(self):
        self.engine = Engine()  # 创建 Engine 类的实例作为 Car 类的属性

    def start(self):
        print("Car starting...")
        self.engine.start()  # 调用 Engine 类的方法

    def stop(self):
        print("Car stopping...")
        self.engine.stop()  # 调用 Engine 类的方法

car = Car()
car.start()  # 输出: Car starting... \n Engine started
car.stop()   # 输出: Car stopping... \n Engine stopped
```

在这个示例中，`Car` 类包含了一个 `Engine` 类的实例作为其属性。通过组合，`Car` 类可以利用 `Engine` 类的 `start` 和 `stop` 方法来实现汽车的启动和停止功能。