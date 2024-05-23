以下是Python中Turtle模块的一些常用方法，并附带了代码演示：

```python
import turtle

# 创建Turtle对象
t = turtle.Turtle()

# 基本移动方法
t.forward(100)  # 向前移动100个单位
t.backward(100)  # 向后移动100个单位
t.right(90)  # 向右旋转90度
t.left(90)  # 向左旋转90度

# 画笔控制方法
t.penup()  # 抬起画笔，不绘制轨迹
t.pendown()  # 放下画笔，开始绘制轨迹
t.pensize(2)  # 设置画笔宽度
t.pencolor("red")  # 设置画笔颜色
t.fillcolor("blue")  # 设置填充颜色

# 形状控制方法
t.shape("turtle")  # 设置Turtle的形状
t.speed(1)  # 设置绘制速度，1最慢，10最快

# 绘制图形
t.circle(50)  # 绘制一个半径为50的圆
t.goto(0, 0)  # 移动到坐标(0, 0)
t.dot(30, "green")  # 绘制一个半径为30的绿色点
t.stamp()  # 在当前位置绘制一个克隆图像

# 填充图形
t.begin_fill()  # 标记填充图形的起始点
for _ in range(4):
    t.forward(100)
    t.right(90)
t.end_fill()  # 标记填充图形的结束点

# 退出Turtle图形界面
turtle.bye()
```

这些方法可以让你创建各种形状和图案，你可以根据需要组合它们以实现不同的绘图效果。

```python
# 控制Turtle方向
t.setheading(45)  # 设置Turtle的朝向为45度
t.left(45)  # 向左旋转45度
t.right(45)  # 向右旋转45度

# 绘制多边形
t.begin_fill()
for _ in range(6):
    t.forward(50)
    t.right(60)
t.end_fill()

# 控制画笔
t.penup()
t.goto(100, 100)
t.pendown()

# 清空画布
t.clear()

# 隐藏/显示Turtle
t.hideturtle()
t.showturtle()

# 控制窗口
turtle.bgcolor("lightblue")  # 设置背景颜色
turtle.title("My Turtle Drawing")  # 设置窗口标题

# 控制窗口的大小
turtle.setup(width=800, height=600)

# 延迟关闭窗口
turtle.mainloop()
```

这些方法可以帮助你更好地控制Turtle图形的行为，从而实现各种绘图效果。你可以根据需要将它们组合起来创建自己的图形。