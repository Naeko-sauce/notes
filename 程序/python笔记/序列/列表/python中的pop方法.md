在 Python 中，`pop()` 是列表（List）和字典（Dictionary）常用的方法之一，它用于移除并返回指定位置（对于列表）或键（对于字典）的元素。下面是 `pop()` 在列表和字典中的用法详细说明：

### 在列表中使用 `pop()`

在列表中，`pop()` 方法用于移除并返回指定位置的元素。它的语法如下：

```python
list.pop([index])
```

- `index`（可选参数）：要移除的元素的索引。如果不提供索引，默认移除并返回列表的最后一个元素。

#### 示例：

```python
my_list = [1, 2, 3, 4, 5]

# 移除并返回最后一个元素
removed_element = my_list.pop()
print(removed_element)  # 输出: 5
print(my_list)          # 输出: [1, 2, 3, 4]

# 移除并返回索引为 1 的元素
removed_element = my_list.pop(1)
print(removed_element)  # 输出: 2
print(my_list)          # 输出: [1, 3, 4]
```

### 在字典中使用 `pop()`

在字典中，`pop()` 方法用于移除并返回指定键的元素。它的语法如下：

```python
dictionary.pop(key[, default])
```

- `key`：要移除的元素的键。
- `default`（可选参数）：如果键不存在，返回默认值。如果不提供，默认情况下会引发 KeyError。

#### 示例：

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

# 移除并返回键为 'b' 的元素
removed_value = my_dict.pop('b')
print(removed_value)  # 输出: 2
print(my_dict)         # 输出: {'a': 1, 'c': 3}

# 使用默认值，移除并返回键为 'x' 的元素
removed_value = my_dict.pop('x', 'Key not found')
print(removed_value)  # 输出: 'Key not found'
```

总体而言，`pop()` 是一种方便的方法，可以在不知道列表或字典长度的情况下移除并返回元素。在使用时，请确保提供正确的索引或键，以避免出现 `IndexError` 或 `KeyError`。****