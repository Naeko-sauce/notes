在 Python 中，可以使用 `center()`、`ljust()` 和 `rjust()` 方法来对字符串进行居中、左对齐和右对齐。

1. `center()` 方法用于将字符串居中排版，可以指定字符串的总长度以及用于填充的字符（默认为空格）。
   ```python
   s = "hello"
   centered_s = s.center(10, '*')
   print(centered_s)  # 输出: "**hello***"
   ```

2. `ljust()` 方法用于将字符串左对齐排版，同样可以指定字符串的总长度和填充字符（默认为空格）。
   ```python
   s = "hello"
   left_justified_s = s.ljust(10, '*')
   print(left_justified_s)  # 输出: "hello*****"
   ```

3. `rjust()` 方法用于将字符串右对齐排版，同样可以指定字符串的总长度和填充字符（默认为空格）。
   ```python
   s = "hello"
   right_justified_s = s.rjust(10, '*')
   print(right_justified_s)  # 输出: "*****hello"
   ```

希望这些说明能够帮助到你。