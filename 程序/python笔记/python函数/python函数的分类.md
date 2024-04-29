Python 中的函数可以根据其定义和使用方式进行分类。以下是一些常见的函数分类及其示例：

### 1. 内置函数 (Built-in Functions)
这些函数是 Python 解释器中内置的，可以直接使用，无需导入其他模块。

**示例：**
```python
# 使用内置函数 len() 获取列表长度
my_list = [1, 2, 3, 4, 5]
length = len(my_list)
print(length)  # 输出: 5

# 使用内置函数 range() 生成一个范围内的整数序列
for i in range(5):
    print(i)  # 输出: 0, 1, 2, 3, 4
```

### 2. 用户自定义函数 (User-defined Functions)
这些函数由用户自行定义，用于完成特定任务。

**示例：**
```python
# 定义一个简单的用户自定义函数
def greet(name):
    print(f"Hello, {name}!")

# 调用该函数
greet("Alice")  # 输出: Hello, Alice!
```

### 3. 匿名函数 (Lambda Functions)
使用 `lambda` 关键字定义的小型、临时的函数。

**示例：**
```python
# 使用 lambda 创建一个加法函数
add = lambda x, y: x + y
result = add(3, 5)
print(result)  # 输出: 8
```

### 4. 递归函数 (Recursive Functions)
函数内部调用自身的函数。

**示例：**
```python
# 使用递归计算阶乘
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

result = factorial(5)
print(result)  # 输出: 120
```

### 5. 高阶函数 (Higher-Order Functions)
可以接受函数作为参数或将函数作为返回值的函数。

**示例：**
```python
# 接受函数作为参数的高阶函数
def apply_operation(operation, x, y):
    return operation(x, y)

def multiply(a, b):
    return a * b

result = apply_operation(multiply, 3, 4)
print(result)  # 输出: 12
```

### 6. 生成器函数 (Generator Functions)
使用 `yield` 语句来生成值的函数，可以用于迭代器。

**示例：**
```python
# 使用生成器函数生成斐波那契数列
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

fib = fibonacci()
for _ in range(10):
    print(next(fib))  # 输出: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34
```

这些是 Python 中常见的函数分类和示例。根据需要，函数可以结合这些特性进行灵活的设计和使用。