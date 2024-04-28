`continue` 是 Python 中的一个循环控制语句，用于跳过当前迭代中剩余的代码，并继续下一次迭代。当程序执行到 `continue` 语句时，会立即结束当前迭代，然后回到循环的顶部，开始下一次迭代。

### 使用 `continue` 的作用和示例

使用 `continue` 的主要作用是在循环体中根据特定条件跳过部分代码，而不是立即退出整个循环。

**示例 1：跳过偶数**

下面的示例演示了如何使用 `continue` 跳过列表中的偶数，只打印奇数：

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

for num in numbers:
    if num % 2 == 0:
        continue  # 如果是偶数，跳过本次迭代，继续下一次迭代
    print(num)
```

**输出**：
```
1
3
5
7
9
```

在上面的示例中，当 `num` 是偶数时，`continue` 语句会跳过 `print(num)` 这行代码，直接进入下一次循环。因此，只有奇数会被打印出来。

**示例 2：避免处理特定值**

另一个示例是在循环中遇到特定值时跳过处理：

```python
values = [10, 20, -1, 30, 40, -1, 50]

for value in values:
    if value == -1:
        continue  # 跳过处理值为 -1 的情况
    # 对其他值进行处理
    print(f"Processing value: {value}")
```

**输出**：
```
Processing value: 10
Processing value: 20
Processing value: 30
Processing value: 40
Processing value: 50
```

在这个示例中，当循环遇到值为 `-1` 的元素时，`continue` 语句会跳过打印和处理这个值，直接进入下一次迭代。

总之，`continue` 语句用于跳过当前迭代中的代码，直接进行下一次迭代。这对于在循环中根据特定条件避免执行部分代码非常有用。