Python 中字符串的常用查找方法包括 `len()`、`startswith()`、`endswith()`、`find()`、`rfind()`、`count()` 和 `isalnum()`。

- `len()`: 用于返回字符串的长度。
- `startswith()`: 用于检查字符串是否以指定的子字符串开头，如果是则返回 True，否则返回 False。
- `endswith()`: 用于检查字符串是否以指定的子字符串结尾，如果是则返回 True，否则返回 False。
- `find()`: 用于查找子字符串在原字符串中的位置，如果找到则返回第一次出现的索引，如果找不到则返回-1。
- `rfind()`: 与 `find()` 类似，不过是从右边开始查找。
- `count()`: 用于统计子字符串在原字符串中出现的次数。
- `isalnum()`: 用于检查字符串是否由字母和数字组成，如果是则返回 True，否则返回 False。

下面是这些方法的简单示例：

```python
s = "Hello, World!"

# 使用len()方法获取字符串长度
print(len(s))  # 输出: 13

# 使用startswith()和endswith()方法检查字符串开头和结尾
print(s.startswith("Hello"))  # 输出: True
print(s.endswith("World!"))  # 输出: True

# 使用find()和rfind()方法查找子字符串
print(s.find("o"))  # 输出: 4
print(s.rfind("o"))  # 输出: 8

# 使用count()方法统计子字符串出现的次数
print(s.count("l"))  # 输出: 3

# 使用isalnum()方法检查字符串是否由字母和数字组成
print(s.isalnum())  # 输出: False
```

希望这些信息能够帮助到你。