### 守护线程（Daemon Thread）

守护线程是一种特殊类型的线程，它在后台运行，主要用于执行一些后台任务。当所有非守护线程（通常是主线程）结束时，守护线程会被强制终止。它的主要用途是在程序退出时不需要等待这些线程完成。

#### 如何创建守护线程：

- **设置方式**：在创建线程对象后，将 `daemon` 属性设置为 `True`。

#### 示例代码：

```python
import threading
import time

def background_task():
    while True:
        print("守护线程正在运行...")
        time.sleep(1)

# 创建守护线程
daemon_thread = threading.Thread(target=background_task)
daemon_thread.daemon = True  # 设置为守护线程
daemon_thread.start()

# 主线程
for i in range(5):
    print("主线程正在运行...")
    time.sleep(1)

print("主线程结束，守护线程也会随之结束。")
```

在上面的示例中，守护线程在主线程结束后自动终止，而不需要明确的结束指令。

### `join()` 方法

`join()` 方法用于在主线程中等待某个线程完成。调用这个方法时，主线程将阻塞，直到调用 `join()` 的线程完成。它在需要确保某些任务完成后再继续执行的场景中非常有用。

#### 示例代码：

```python
import threading
import time

def worker():
    print("线程开始工作...")
    time.sleep(2)  # 模拟工作
    print("线程工作完成。")

# 创建线程
thread = threading.Thread(target=worker)
thread.start()

# 主线程等待子线程完成
thread.join()  # 等待子线程完成

print("子线程已完成，主线程继续执行。")
```

在这个示例中，主线程会在子线程 `worker()` 执行完毕后再继续打印信息。

### 关键区别

- **使用场景**：
  - **守护线程**：适用于不需要等待的后台任务，比如日志记录、定时任务等。
  - **`join()`**：适用于需要确保某个线程完成后再继续的场合，如确保数据处理完成再进行后续操作。

- **生命周期**：
  - 守护线程在所有非守护线程结束后自动结束。
  - 使用 `join()` 的线程需要显式地调用，主线程会等待它完成。

### 选择合适的方式

- 如果你的程序需要在后台进行一些无关紧要的工作，可以选择守护线程。
- 如果你的程序依赖某些线程的结果，使用 `join()` 来确保执行顺序。

这两者在多线程编程中各有用途，可以根据具体需求灵活使用。