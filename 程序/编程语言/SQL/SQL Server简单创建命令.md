在SQL Server中，创建数据库涉及到一系列的命令和选项。以下是创建SQL Server数据库的详细说明：

1. **CREATE DATABASE**：这是创建数据库的主要命令。基本语法如下：

   ```sql
   CREATE DATABASE database_name;
   ```

   - `database_name`：要创建的数据库的名称。

2. **ON PRIMARY**：此选项用于指定数据库文件的物理文件名、大小和文件组。示例：

   ```sql
   ON PRIMARY
   ( 
       NAME = logical_name,  -- 逻辑文件名
       FILENAME = 'file_path' -- 物理文件路径
       SIZE = size,           -- 初始文件大小
       MAXSIZE = max_size,    -- 最大文件大小
       FILEGROWTH = growth    -- 文件增长大小
   )
   ```

   - `logical_name`：逻辑文件名，用于标识文件。
   - `file_path`：物理文件路径，表示数据库文件将存储在哪个位置。
   - `size`：初始文件大小，指定文件的初始大小。
   - `max_size`：最大文件大小，文件的最大尺寸限制。
   - `growth`：文件增长大小，文件自动增长时的大小。

3. **LOG ON**：此选项用于指定日志文件的物理文件名、大小和文件组。示例：

   ```sql
   LOG ON
   ( 
       NAME = logical_name,  -- 逻辑文件名
       FILENAME = 'file_path' -- 物理文件路径
       SIZE = size,           -- 初始文件大小
       MAXSIZE = max_size,    -- 最大文件大小
       FILEGROWTH = growth    -- 文件增长大小
   )
   ```

   - `logical_name`：逻辑文件名，用于标识日志文件。
   - `file_path`：物理文件路径，表示日志文件将存储在哪个位置。
   - `size`：初始文件大小，指定日志文件的初始大小。
   - `max_size`：最大文件大小，日志文件的最大尺寸限制。
   - `growth`：文件增长大小，日志文件自动增长时的大小。

4. **COLLATE**：此选项用于指定数据库的排序规则（Collation）。示例：

   ```sql
   COLLATE collation_name
   ```

   - `collation_name`：要使用的排序规则的名称。

5. **DATABASE**：此选项用于指定数据库的其他属性，如状态、复制选项等。示例：

   ```sql
   DATABASEPROPERTIES (
       property_name = property_value,
       ...
   )
   ```

   - `property_name`：属性名称，如`ALLOW_SNAPSHOT_ISOLATION`、`READ_COMMITTED_SNAPSHOT`等。
   - `property_value`：属性的值。

6. **CONTAINMENT = PARTIAL**：此选项用于启用数据库的部分隔离性。示例：

   ```sql
   CONTAINMENT = PARTIAL;
   ```

7. **WITH**：此选项用于指定其他数据库选项，如文件初始化选项、文件夹选项等。示例：

   ```sql
   WITH 
   {
       FILESTREAM ( 
           NON_TRANSACTED_ACCESS = access_type,
           DIRECTORY_NAME = directory_name
       )
   }
   ```

   - `access_type`：Filestream 访问类型，可以是 READ_ONLY 或 FULL。
   - `directory_name`：Filestream 文件夹的名称。

8. **Example**：以下是创建数据库的完整示例：

   ```sql
   CREATE DATABASE MyDatabase
   ON PRIMARY
   ( 
       NAME = MyDatabaseData, 
       FILENAME = 'C:\SQLData\MyDatabaseData.mdf',
       SIZE = 10MB,
       MAXSIZE = 100MB,
       FILEGROWTH = 5MB
   )
   LOG ON
   ( 
       NAME = MyDatabaseLog,
       FILENAME = 'C:\SQLData\MyDatabaseLog.ldf',
       SIZE = 5MB,
       MAXSIZE = 50MB,
       FILEGROWTH = 5MB
   )
   COLLATE SQL_Latin1_General_CP1_CI_AS;
   ```

   这个示例创建了一个名为"MyDatabase"的数据库，具有指定的数据文件和日志文件的物理路径、大小和增长选项，以及指定的排序规则。

请注意，上述示例仅涵盖了创建数据库的基本选项。根据您的需求，可以使用更多选项和属性来自定义数据库的创建过程。