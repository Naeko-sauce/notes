在Python中，你可以使用字符串格式化来将数字格式化为特定的样式或形式，以便更容易阅读或展示。字符串格式化的方式有多种，其中两种常见的方法是使用百分号（%）操作符和使用字符串的`format()`方法。下面我将详细说明这两种方法：

### 1. 百分号（%）格式化

使用百分号（%）操作符是一种传统的字符串格式化方法，它类似于C语言中的格式化字符串。你可以使用不同的格式标志将数字格式化为不同的形式。

- `%d`：整数格式化
- `%f`：浮点数格式化
- `%s`：字符串格式化
- `%x`：十六进制整数格式化

示例：

```python
# 整数格式化
age = 25
formatted_age = "My age is %d" % age
print(formatted_age)  # 输出："My age is 25"

# 浮点数格式化
pi = 3.141592653589793
formatted_pi = "The value of pi is %.2f" % pi
print(formatted_pi)  # 输出："The value of pi is 3.14"

# 字符串格式化
name = "Alice"
formatted_name = "Hello, %s!" % name
print(formatted_name)  # 输出："Hello, Alice!"

# 十六进制整数格式化
number = 255
formatted_number = "The number in hex is %x" % number
print(formatted_number)  # 输出："The number in hex is ff"
```

### 2. `format()` 方法格式化

使用`format()`方法进行字符串格式化更加灵活，因为你可以在字符串中使用占位符 `{}`，然后使用`format()`方法传递要插入的值。你可以指定要格式化的值的顺序，并使用格式规范指定格式。

示例：

```python
# 基本的格式化
name = "Bob"
age = 30
formatted_text = "My name is {} and I am {} years old.".format(name, age)
print(formatted_text)  # 输出："My name is Bob and I am 30 years old."

# 使用位置参数
formatted_text = "My name is {0} and I am {1} years old.".format(name, age)
print(formatted_text)  # 输出："My name is Bob and I am 30 years old."

# 使用关键字参数
formatted_text = "My name is {name} and I am {age} years old.".format(name="Alice", age=25)
print(formatted_text)  # 输出："My name is Alice and I am 25 years old."

# 指定格式
pi = 3.141592653589793
formatted_pi = "The value of pi is {:.2f}".format(pi)
print(formatted_pi)  # 输出："The value of pi is 3.14"
```

这是两种常见的字符串格式化方法，你可以根据需求选择其中一种来格式化数字和其他数据类型。`format()`方法通常被认为是更现代和推荐的方法，因为它更加灵活，易于维护，并且支持更多的格式化选项。