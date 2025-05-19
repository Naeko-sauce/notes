在 Python 中，类的继承是一种强大的特性，允许一个类从另一个类继承属性和方法。要查看类的继承情况，可以使用多种方法和工具，包括内置函数、模块以及反射机制。下面详细介绍如何查看类的继承关系，并举例说明。

### 查看类的继承关系

1. **使用 `__bases__` 属性**：
   - 这是一个元组，包含直接基类。
2. **使用 `issubclass()` 函数**：
   - 检查一个类是否是另一个类的子类。
3. **使用 `super()` 函数**：
   - 调用父类的方法。
4. **使用 `mro()` 方法**：
   - 查看类的方法解析顺序（MRO）。
5. **使用 `inspect` 模块**：
   - 获取更多关于类的信息。

### 示例代码

#### 使用 `__bases__` 属性

```python
class A:
    pass

class B(A):
    pass

class C(B):
    pass

print(B.__bases__)  # 输出：(A,)
print(C.__bases__)  # 输出：(B,)
```

#### 使用 `issubclass()` 函数

```python
print(issubclass(B, A))  # 输出：True
print(issubclass(C, A))  # 输出：True
print(issubclass(C, B))  # 输出：True
print(issubclass(A, B))  # 输出：False
```

#### 使用 `super()` 函数

```python
class Parent:
    def __init__(self):
        print("Parent init")

    def method(self):
        print("Parent method")

class Child(Parent):
    def __init__(self):
        super().__init__()  # 调用父类的构造函数
        print("Child init")

    def method(self):
        super().method()  # 调用父类的方法
        print("Child method")

child = Child()
child.method()
```

#### 使用 `mro()` 方法

```python
print(C.mro())  
# 输出：[<class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>]
```

#### 使用 `inspect` 模块

```python
import inspect

class D(C):
    pass

print(inspect.getmro(D))
# 输出：(<class '__main__.D'>, <class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>)
```

### 详细说明

1. **`__bases__` 属性**：
    - 用于获取一个类的直接基类。
    - 例如，`B.__bases__` 返回 `(A,)`，表示 `B` 直接继承自 `A`。

2. **`issubclass()` 函数**：
    - 用于检查一个类是否是另一个类的子类。
    - 例如，`issubclass(C, A)` 返回 `True`，表示 `C` 是 `A` 的子类（无论是直接继承还是间接继承）。

3. **`super()` 函数**：
    - 用于调用父类的方法。
    - 在子类中使用 `super()` 可以调用父类的构造函数或其他方法。

4. **`mro()` 方法**：
    - 用于获取类的方法解析顺序（MRO）。
    - MRO 定义了类的继承层次和方法查找顺序，`C.mro()` 返回一个列表，表示从 `C` 类开始到 `object` 类的继承链。

5. **`inspect` 模块**：
    - `inspect.getmro()` 函数返回一个类的继承层次结构。
    - 例如，`inspect.getmro(D)` 返回 `(<class '__main__.D'>, <class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>)`，表示 `D` 继承自 `C`，`C` 继承自 `B`，以此类推。

通过这些方法，可以方便地查看类的继承关系，了解类的层次结构和方法解析顺序，有助于调试和理解代码。