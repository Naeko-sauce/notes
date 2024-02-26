`strip()` 和 `lstrip()` 是 Python 中用于去除字符串首尾信息的方法。

- `strip()` 会去除字符串开头和结尾的空格或指定的字符。
- `lstrip()` 会去除字符串开头的空格或指定的字符，但不会影响字符串结尾的部分。

下面是这两个方法的简单示例：

```python
s = "  Hello, World!  "
trimmed_s = s.strip()
left_trimmed_s = s.lstrip()
print(trimmed_s)  # 输出: "Hello, World!"
print(left_trimmed_s)  # 输出: "Hello, World!  "
```