`strip()`、`lstrip()` 和 `rstrip()` 是 Python 中用于去除字符串首尾信息的方法。

- `strip()` 方法会去除字符串开头和结尾的空格或指定的字符。
- `lstrip()` 方法会去除字符串开头的空格或指定的字符，但不会影响字符串结尾的部分。
- `rstrip()` 方法会去除字符串结尾的空格或指定的字符，但不会影响字符串开头的部分。

下面是这三个方法的简单示例：

```python
s = "  Hello, World!  "
trimmed_s = s.strip()
left_trimmed_s = s.lstrip()
right_trimmed_s = s.rstrip()
print(trimmed_s)  # 输出: "Hello, World!"
print(left_trimmed_s)  # 输出: "Hello, World!  "
print(right_trimmed_s)  # 输出: "  Hello, World!"
```
