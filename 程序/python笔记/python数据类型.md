Python 是一种动态类型语言，允许你在运行时创建和操作不同数据类型的对象。以下是Python中一些常见的数据类型：

1. **整数（int）**:
   - 用于表示整数值，例如：-1、0、1、100等。
   - 示例：
     ```python
     x = 42
     ```

2. **浮点数（float）**:
   - 用于表示带有小数部分的数值，例如：3.14、0.0、-2.5等。
   - 示例：
     ```python
     pi = 3.14159
     ```

3. **字符串（str）**:
   - 用于表示文本数据，可以使用单引号或双引号括起来。
   - 示例：
     ```python
     message = "Hello, World!"
     ```

4. **布尔值（bool）**:
   - 用于表示逻辑值，只有两个取值：`True` 和 `False`。
   - 示例：
     ```python
     is_true = True
     is_false = False
     ```

5. **列表（list）**:
   - 用于存储一组有序的元素，元素可以是不同类型的。
   - 示例：
     ```python
     numbers = [1, 2, 3, 4, 5]
     fruits = ["apple", "banana", "cherry"]
     ```

6. **元组（tuple）**:
   - 类似于列表，但是元组是不可变的，一旦创建就不能修改。
   - 示例：
     ```python
     point = (3, 4)
     ```

7. **字典（dict）**:
   - 用于存储键值对，每个键都是唯一的。
   - 示例：
     ```python
     person = {"name": "Alice", "age": 30}
     ```

8. **集合（set）**:
   - 用于存储一组唯一的元素，通常用于去重。
   - 示例：
     ```python
     unique_numbers = {1, 2, 3, 4, 5}
     ```

9. **NoneType**:
   - 用于表示空值或缺少值的对象，通常表示一个变量未初始化。
   - 示例：
     ```python
     empty_value = None
     ```

10. **自定义类（class）**:
    - 你可以创建自定义的类来表示复杂的数据结构，包括属性和方法。
    - 示例：
      ```python
      class Person:
          def __init__(self, name, age):
              self.name = name
              self.age = age
      ```

这些是Python中一些常见的数据类型，你可以根据需求使用不同类型的对象来处理各种数据。 Python还支持其他一些高级数据类型和标准库模块，如日期时间、文件、正则表达式等。