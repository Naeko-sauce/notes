在 Python 中，有几种方法可以用于字符串大小写转换。以下是所有方法的详细说明：

1. `upper()`: 将字符串中的所有字母转换为大写。
   ```python
   s = "hello, world!"
   upper_s = s.upper()
   print(upper_s)  # 输出: "HELLO, WORLD!"
   ```

2. `lower()`: 将字符串中的所有字母转换为小写。
   ```python
   s = "Hello, World!"
   lower_s = s.lower()
   print(lower_s)  # 输出: "hello, world!"
   ```

3. `capitalize()`: 将字符串的第一个字符转换为大写，其他字符转换为小写。
   ```python
   s = "hello, world!"
   capitalized_s = s.capitalize()
   print(capitalized_s)  # 输出: "Hello, world!"
   ```

4. `title()`: 将字符串中每个单词的首字母转换为大写，其他字母转换为小写。
   ```python
   s = "hello, world!"
   titled_s = s.title()
   print(titled_s)  # 输出: "Hello, World!"
   ```

5. `swapcase()`: 将字符串中的大写字母转换为小写，小写字母转换为大写。
   ```python
   s = "Hello, World!"
   swapped_s = s.swapcase()
   print(swapped_s)  # 输出: "hELLO, wORLD!"
   ```

希望这些详细说明能够帮助到你。