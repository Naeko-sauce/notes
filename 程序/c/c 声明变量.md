在 C 语言中，变量是用于存储数据的一种标识符。在使用变量之前，需要先声明它们，并指定它们的数据类型。以下是一些关于 C 语言变量的基本知识：

1. **变量声明：**
   在 C 语言中，变量的声明告诉编译器在内存中为变量分配空间。声明的一般形式为：
   ```c
   data_type variable_name;
   ```

   例如：
   ```c
   int age;
   float salary;
   char grade;
   ```

2. **变量初始化：**
   变量可以在声明的同时进行初始化，即为变量赋初值。例如：
   ```c
   int age = 25;
   float salary = 50000.50;
   char grade = 'A';
   ```

   或者可以在后续的代码中进行赋值：
   ```c
   age = 30;
   salary = 60000.75;
   grade = 'B';
   ```

3. **数据类型：**
   C 语言中有各种数据类型，包括整数类型（int、short、long）、浮点类型（float、double）、字符类型（char）等。例如：
   ```c
   int num = 42;
   float pi = 3.14;
   char letter = 'A';
   ```

4. **变量命名规则：**
   - 变量名由字母、数字和下划线组成。
   - 变量名必须以字母或下划线开头。
   - 变量名对大小写敏感。
   - 不能使用 C 语言的关键字作为变量名。

   例如：
   ```c
   int myVariable;
   float average_score;
   ```

5. **示例：**
   下面是一个简单的 C 语言程序，演示了变量的声明和使用：
   ```c
   #include <stdio.h>

   int main() {
       int age = 25;
       float salary = 50000.50;

       printf("Age: %d\n", age);
       printf("Salary: %.2f\n", salary);

       return 0;
   }
   ```

   在上述示例中，`age` 和 `salary` 分别是整数和浮点数类型的变量，用于存储年龄和工资信息。