Python 中的时间模块是 `time` 模块，它提供了与时间相关的各种功能，包括获取当前时间、日期格式化、暂停程序执行等。以下是 `time` 模块中一些常用的功能和函数：

1. **获取当前时间戳：**
   - `time.time()`: 返回当前时间的时间戳，即自 1970 年 1 月 1 日午夜以来的秒数。

    ```python
    import time

    current_timestamp = time.time()
    print(current_timestamp)
    ```

2. **获取当前时间的结构化表示：**
   - `time.localtime()`: 返回当前时间的本地时间结构。

    ```python
    import time

    local_time = time.localtime()
    print(local_time)
    ```

3. **格式化时间：**
   - `time.strftime(format, time_struct)`: 根据给定的格式化字符串，将时间元组格式化为字符串。

    ```python
    import time

    current_time = time.localtime()
    formatted_time = time.strftime("%Y-%m-%d %H:%M:%S", current_time)
    print(formatted_time)
    ```

4. **休眠（延迟执行）：**
   - `time.sleep(seconds)`: 暂停程序执行指定秒数。

    ```python
    import time

    print("Start")
    time.sleep(2)  # 暂停2秒
    print("End")
    ```

5. **计时器：**
   - `time.perf_counter()`: 返回一个精确的计时器，用于测量时间间隔。

    ```python
    import time

    start_time = time.perf_counter()
    # 执行一些操作
    end_time = time.perf_counter()

    elapsed_time = end_time - start_time
    print(f"Elapsed Time: {elapsed_time} seconds")
    ```

这只是 `time` 模块提供的一部分功能。对于更复杂的时间操作，还可以考虑使用 `datetime` 模块，它提供了更多的日期和时间处理功能。