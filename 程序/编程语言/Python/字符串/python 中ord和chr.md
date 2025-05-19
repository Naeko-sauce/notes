# Python 中的 ord ()和 chr ()函数

## Ord ()函数
- `ord()` 函数接受一个 Unicode 字符的字符串参数，并返回其整数 Unicode 代码点值。
- 例如：`ord('A')` 将返回 65，代表字符'A'的 Unicode 代码点值。

## Chr ()函数
- `chr()` 函数接受整数参数，并返回表示该代码点处字符的字符串。
- 例如：`chr(65)` 将返回'A'，代表 Unicode 代码点 65 处的字符。

## 示例
```python
x = ord('A')
print(x)

print(ord('ć'))
print(ord('ç'))
print(ord('$'))

y = chr(65)
print(y)
print(chr(123))
print(chr(36))

print(chr(ord('ć')))
print(ord(chr(65)))
```

输出：
```
65
263
231
36
A
{
$
ć
65
```

这些函数是互为相反的，因此 `ord(chr(x))` 将返回 `x`，`chr(ord(c))` 将返回 `c`。这些函数非常有用，可以在处理字符和整数之间进行转换。