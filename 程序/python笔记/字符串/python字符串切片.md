Python 中常用的字符串切片方法有六种，分别是：

1. 使用索引进行切片：
   ```python
   s = "Hello, World!"
   print(s[7:])  # 输出: "World!"
   ```

2. 使用 slice ()函数：
   ```python
   s = "Hello, World!"
   slice_object = slice(7, None)
   print(s[slice_object])  # 输出: "World!"
   ```

3. 使用负索引进行切片：
   ```python
   s = "Hello, World!"
   print(s[-6:])  # 输出: "World!"
   ```

4. 使用步长进行切片：
   ```python
   s = "Hello, World!"
   print(s[7:12:2])  # 输出: "Wrd"
   ```

5. 使用负索引和步长进行切片：
   ```python
   s = "Hello, World!"
   print(s[-1:-6:-1])  # 输出: "dlroW"
   ```

6. 使用空参数进行切片：
   ```python
   s = "Hello, World!"
   print(s[:5])  # 输出: "Hello"
   ```

希望这些方法能够满足你的需求。