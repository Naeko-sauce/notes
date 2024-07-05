这段代码是一个使用 `tkinter` 库创建的简单的图形用户界面 (GUI) 应用程序，包含一个按钮，当按钮被点击时，会弹出一个消息框。以下是每一部分代码的解释：

```python
import tkinter
from tkinter import *
from tkinter import messagebox
```
- `import tkinter`: 导入 `tkinter` 模块，用于创建 GUI 应用程序。
- `from tkinter import *`: 从 `tkinter` 模块中导入所有的类和函数，便于直接使用。
- `from tkinter import messagebox`: 从 `tkinter` 模块中导入 `messagebox` 类，用于显示消息框。

```python
root = tkinter.Tk()
```
- `root = tkinter.Tk()`: 创建一个 `Tk` 窗口实例，这是应用程序的主窗口。

```python
but = Button(root)
but['text'] = 'Hello World'
but.pack()
```
- `but = Button(root)`: 创建一个按钮组件，父容器是 `root` 窗口。
- `but['text'] = 'Hello World'`: 设置按钮的显示文本为 "Hello World"。
- `but.pack()`: 将按钮添加到窗口中，并自动调整其大小和位置。

```python
def hello(e):
  messagebox.showinfo("Hello World", e)
```
- `def hello(e)`: 定义一个事件处理函数 `hello`，接收事件对象 `e` 作为参数。
- `messagebox.showinfo("Hello World", e)`: 显示一个消息框，标题为 "Hello World"，内容为事件对象 `e`。

```python
but.bind("<Button-1>", hello)
```
- `but.bind("<Button-1>", hello)`: 绑定按钮的左键单击事件到 `hello` 函数。即当按钮被左键单击时，调用 `hello` 函数。

```python
root.mainloop()
```
- `root.mainloop()`: 启动 `tkinter` 的事件循环，使窗口保持显示状态并响应用户的输入。

### 总结

这个程序创建了一个包含 "Hello World" 按钮的 GUI 窗口。当用户点击按钮时，会弹出一个消息框显示事件信息。通过 `root.mainloop()`，程序进入事件循环，持续运行，直到用户关闭窗口。

# 完整代码
```python
import tkinter  
from tkinter import *  
from tkinter import messagebox  
  
root = tkinter.Tk()  
but = Button(root)  
but['text'] = 'Hello World'  
  
but.pack()  
def hello(e):  
  messagebox.showinfo("Hello World", e)  
root.mainloop() #使用此方法，进入事件循环
```