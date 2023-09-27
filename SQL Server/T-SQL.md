T-SQL（Transact-SQL）是用于管理和查询关系数据库的编程语言，主要用于Microsoft SQL Server（MSSQL）数据库系统。以下是一些T-SQL的常见用途和一些常见指令的详细说明：

1. **查询数据 (SELECT)**
   - 用途：从一个或多个表中检索数据。
   - 示例：
     ```sql
     SELECT FirstName, LastName FROM Employees WHERE DepartmentID = 101;
     ```
   
2. **插入数据 (INSERT)**
   - 用途：向表中插入新的行。
   - 示例：
     ```sql
     INSERT INTO Employees (EmployeeID, FirstName, LastName, BirthDate, DepartmentID)
     VALUES (1, 'John', 'Doe', '1990-01-15', 101);
     ```

3. **更新数据 (UPDATE)**
   - 用途：更新表中的现有数据。
   - 示例：
     ```sql
     UPDATE Employees SET DepartmentID = 102 WHERE EmployeeID = 1;
     ```

4. **删除数据 (DELETE)**
   - 用途：从表中删除行。
   - 示例：
     ```sql
     DELETE FROM Employees WHERE EmployeeID = 1;
     ```

5. **创建表 (CREATE TABLE)**
   - 用途：创建新的数据库表。
   - 示例：
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         FirstName NVARCHAR(50),
         LastName NVARCHAR(50),
         BirthDate DATE,
         DepartmentID INT
     );
     ```

6. **创建存储过程 (CREATE PROCEDURE)**
   - 用途：创建可重复使用的T-SQL代码块。
   - 示例：
     ```sql
     CREATE PROCEDURE GetEmployeeByID
         @EmployeeID INT
     AS
     BEGIN
         SELECT * FROM Employees WHERE EmployeeID = @EmployeeID;
     END;
     ```

7. **创建触发器 (CREATE TRIGGER)**
   - 用途：定义在表上执行的自动化操作，通常与数据更改相关。
   - 示例：
     ```sql
     CREATE TRIGGER AuditEmployeeChanges
     ON Employees
     AFTER INSERT, UPDATE, DELETE
     AS
     BEGIN
         -- 触发器逻辑
     END;
     ```

8. **聚合函数 (SUM, AVG, COUNT, MAX, MIN)**
   - 用途：用于计算数据的聚合值。
   - 示例：
     ```sql
     SELECT AVG(Salary) FROM EmployeeSalaries WHERE DepartmentID = 101;
     ```

9. **连接多个表 (JOIN)**
   - 用途：通过将多个表关联在一起来检索相关数据。
   - 示例：
     ```sql
     SELECT Orders.OrderID, Customers.CustomerName
     FROM Orders
     INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
     ```

10. **子查询 (Subquery)**
    - 用途：在查询中嵌套其他查询，用于检索复杂条件下的数据。
    - 示例：
      ```sql
      SELECT ProductName
      FROM Products
      WHERE ProductID IN (SELECT ProductID FROM OrderDetails WHERE OrderID = 123);
      ```

这些是T-SQL中的一些常见用途和指令。T-SQL还包括事务控制、视图、索引、权限管理等其他功能和语法，以支持更复杂的数据库操作和管理任务。它是SQL Server数据库管理的核心工具之一。