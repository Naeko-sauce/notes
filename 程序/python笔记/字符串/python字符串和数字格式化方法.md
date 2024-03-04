Python 中的字符串格式化可以使用 `format()` 方法或者 f-strings 进行。对于数字格式化，可以使用 `format()` 方法或者旧式的 `%` 操作符进行格式化。以下是详细说明：

字符串格式化：
1. 使用 `format()` 方法进行字符串格式化：
   ```python
   name = "Alice"
   age = 25
   formatted_string = "Name: {}, Age: {}".format(name, age)
   print(formatted_string)  # 输出: "Name: Alice, Age: 25"
   ```

2. 使用 f-strings 进行格式化（Python 3.6 及以上版本）：
   ```python
   name = "Alice"
   age = 25
   formatted_string = f"Name: {name}, Age: {age}"
   print(formatted_string)  # 输出: "Name: Alice, Age: 25"
   ```

数字格式化：
1. 使用 `format()` 方法进行数字格式化：
   ```python
   num = 123.456
   formatted_num = "{:.2f}".format(num)
   print(formatted_num)  # 输出: "123.46"
   ```

2. 使用旧式的 `%` 操作符进行数字格式化：
   ```python
   num = 123.456
   formatted_num = "%.2f" % num
   print(formatted_num)  # 输出: "123.46"
   ```

希望这些详细说明能够帮助到你。