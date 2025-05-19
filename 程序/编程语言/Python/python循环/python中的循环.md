当涉及到循环时，Python 提供了多种选项，每种都适用于不同的场景和需求。让我们更详细地了解每种循环，并附上相应的示例。

### 1. For 循环

`for` 循环用于遍历一个可迭代对象（例如列表、元组、字符串等）中的每个元素，并对每个元素执行特定操作，直到迭代结束。

**语法**：
```python
for item in iterable:
    # 执行操作
```

**示例**：
```python
# 遍历列表
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# 遍历字符串
for char in "Python":
    print(char)

# 遍历元组
tuple_nums = (1, 2, 3, 4, 5)
for num in tuple_nums:
    print(num)
```

### 2. While 循环

`while` 循环在条件为真的情况下重复执行循环体内的操作，直到条件变为假为止。

**语法**：
```python
while condition:
    # 执行操作
    # 可能需要修改条件以避免无限循环
```

**示例**：
```python
# 计数器示例
count = 0
while count < 5:
    print(count)
    count += 1
```

### 3. 嵌套循环

在 Python 中，可以在循环内部嵌套另一个循环，以便处理复杂的数据结构或逻辑。

**示例**：
```python
# 嵌套循环遍历二维列表
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for row in matrix:
    for num in row:
        print(num)
```

### 4. 循环控制语句

在循环中，可以使用以下控制语句来改变循环的行为：

- `break`：立即退出循环，不再执行循环体内的剩余代码。
- `continue`：跳过当前迭代的剩余部分，继续下一次迭代。
- `else`：在循环正常结束时执行，但如果循环被 `break` 中断，则不会执行 `else` 块。

**示例**：
```python
# 使用 break 打破循环
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        break
    print(num)  # 输出 1, 2

# 使用 continue 跳过特定迭代
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num % 2 == 0:
        continue
    print(num)  # 输出 1, 3, 5

# 使用循环的 else 块
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 6:
        break
else:
    print("未找到数字 6")  # 输出 "未找到数字 6"，因为循环正常结束没有遇到 break
```

以上是 Python 中常用的循环结构及其示例。选择合适的循环类型取决于具体的任务需求和数据结构。