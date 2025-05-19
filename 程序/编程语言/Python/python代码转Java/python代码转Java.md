要将这段 Python 代码转换为 Java 代码，可以使用 Java 中的封装（encapsulation）特性，通过 private 访问修饰符来限制字段的访问，并提供 public 的 getter 和 setter 方法来访问和修改这些字段。

以下是 Python 代码和它的 Java 等价实现的详细说明：

### Python 代码
```python
class W:
    def __init__(self, name):
        self.__name = name

    @property
    def name(self):
        print(self.__name)
        return self.__name

    @name.setter
    def name(self, name):
        self.__name = name

e = W(199)
print(e.name)
e.name = 2999
print(e.name)
```

### Java 代码
```java
public class W {
    // 私有字段，用于存储name的值
    private int name;

    // 构造函数，用于初始化name字段
    public W(int name) {
        this.name = name;
    }

    // Getter方法，用于获取name字段的值
    public int getName() {
        System.out.println(this.name);  // 打印name的值
        return this.name;
    }

    // Setter方法，用于设置name字段的值
    public void setName(int name) {
        this.name = name;
    }

    public static void main(String[] args) {
        W e = new W(199);  // 创建W类的实例，并初始化name为199
        System.out.println(e.getName());  // 调用getName方法，打印并返回name的值
        e.setName(2999);  // 调用setName方法，将name的值修改为2999
        System.out.println(e.getName());  // 再次调用getName方法，打印并返回新的name值
    }
}
```

### 详细说明
1. **私有字段的定义**:
    ```java
    private int name;
    ```
    这对应于 Python 中的 `self.__name`，表示一个私有字段，只能在类内部访问。

2. **构造函数**:
    ```java
    public W(int name) {
        this.name = name;
    }
    ```
    这对应于 Python 的 `__init__` 方法，用于初始化类的实例。Java 的构造函数与类同名。

3. **Getter 方法**:
    ```java
    public int getName() {
        System.out.println(this.name);
        return this.name;
    }
    ```
    这对应于 Python 中的 `@property` 装饰器。Java 中，通过显式的 `getName` 方法实现 getter。

4. **Setter 方法**:
    ```java
    public void setName(int name) {
        this.name = name;
    }
    ```
    这对应于 Python 中的 `@name.setter` 装饰器。Java 中，通过显式的 `setName` 方法实现 setter。

5. **主方法（main 方法）**:
    ```java
    public static void main(String[] args) {
        W e = new W(199);
        System.out.println(e.getName());
        e.setName(2999);
        System.out.println(e.getName());
    }
    ```
    这部分对应于 Python 中的实例化和方法调用。在 Java 中，`main` 方法是程序的入口点。

通过上述步骤，我们成功地将 Python 代码转换为了等价的 Java 代码，保留了类的封装性和属性的访问控制。