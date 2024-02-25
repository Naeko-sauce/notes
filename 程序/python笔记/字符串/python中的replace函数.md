# Python 中的 replace ()函数

## 功能
- `replace()` 函数用于将字符串中的指定子串替换为新的子串。

## 语法
```python
new_string = old_string.replace(old, new)
```
- `old_string` 是原始字符串
- `old` 是要被替换的子串
- `new` 是要替换成的新子串
- `new_string` 是替换后的新字符串

## 示例
```python
s = "Hello, World!"
new_s = s.replace("Hello", "Bonjour")
print(new_s)  # 输出: "Bonjour, World!"
```

`replace()` 函数非常有用，可以在字符串中进行简单的替换操作，例如将指定的单词或字符替换为其他内容。