Python中有许多用于处理字符串的常用方法。以下是一些常见的字符串方法：

1. `len(str)`：返回字符串的长度。

```python
text = "Hello, World!"
length = len(text)
print(length)  # 输出：13
```

2. `str.lower()` 和 `str.upper()`：将字符串转换为小写或大写。

```python
text = "Hello, World!"
lower_text = text.lower()
upper_text = text.upper()
print(lower_text)  # 输出："hello, world!"
print(upper_text)  # 输出："HELLO, WORLD!"
```

3. `str.strip()`：去除字符串两端的空格和换行符。

```python
text = "   Hello, World!   \n"
stripped_text = text.strip()
print(stripped_text)  # 输出："Hello, World!"
```

4. `str.split(separator)`：根据分隔符将字符串拆分成列表。

```python
text = "apple,banana,cherry"
fruits = text.split(',')
print(fruits)  # 输出：['apple', 'banana', 'cherry']
```

5. `str.join(iterable)`：使用字符串将可迭代对象的元素连接成一个字符串。

```python
fruits = ['apple', 'banana', 'cherry']
text = ','.join(fruits)
print(text)  # 输出："apple,banana,cherry"
```

6. `str.find(substring)` 和 `str.rfind(substring)`：查找子字符串在字符串中的索引位置，前者从左往右查找，后者从右往左查找。

```python
text = "Hello, World!"
index = text.find("World")
print(index)  # 输出：7
```

7. `str.replace(old, new)`：将字符串中的旧子字符串替换为新子字符串。

```python
text = "Hello, World!"
new_text = text.replace("World", "Python")
print(new_text)  # 输出："Hello, Python!"
```

8. `str.startswith(prefix)` 和 `str.endswith(suffix)`：检查字符串是否以特定前缀或后缀开始或结束。

```python
text = "Hello, World!"
starts_with_hello = text.startswith("Hello")
ends_with_world = text.endswith("World")
print(starts_with_hello)  # 输出：True
print(ends_with_world)    # 输出：False
```

这些是一些常见的字符串方法，但Python提供了许多其他方法，可以根据需要进行字符串操作。希望这些示例能够帮助你更好地处理字符串数据。