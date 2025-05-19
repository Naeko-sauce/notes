### `shutil` 模块详细说明及举例

`shutil` 模块是 Python 标准库中的一个用于高级文件操作的模块。它提供了一些对文件和目录进行复制、移动、删除等操作的函数，并支持压缩和解压缩功能。以下是 `shutil` 模块中所有函数的详细说明及举例。

#### 1. 复制操作

- **`shutil.copy(src, dst)`**

  复制文件内容和权限，但不包括元数据（如创建时间、最后修改时间等）。

  ```python
  import shutil

  shutil.copy('source_file.txt', 'destination_file.txt')
  ```

- **`shutil.copy2(src, dst)`**

  复制文件内容、权限和元数据。

  ```python
  import shutil

  shutil.copy2('source_file.txt', 'destination_file.txt')
  ```

- **`shutil.copyfile(src, dst)`**

  仅复制文件内容，不包括权限和元数据。

  ```python
  import shutil

  shutil.copyfile('source_file.txt', 'destination_file.txt')
  ```

- **`shutil.copymode(src, dst)`**

  仅复制权限，不复制内容和元数据。

  ```python
  import shutil

  shutil.copymode('source_file.txt', 'destination_file.txt')
  ```

- **`shutil.copystat(src, dst)`**

  复制元数据（权限、最后访问时间、最后修改时间等），但不复制内容。

  ```python
  import shutil

  shutil.copystat('source_file.txt', 'destination_file.txt')
  ```

- **`shutil.copytree(src, dst, symlinks=False, ignore=None, copy_function=copy2, ignore_dangling_symlinks=False, dirs_exist_ok=False)`**

  递归地复制整个目录树。如果 `dirs_exist_ok` 设置为 `True`，则目标目录已经存在时不会报错。

  ```python
  import shutil

  shutil.copytree('source_dir', 'destination_dir')
  ```

#### 2. 移动和重命名操作

- **`shutil.move(src, dst)`**

  移动文件或目录到新的位置。如果目标位置存在同名文件或目录，将会覆盖。

  ```python
  import shutil

  shutil.move('source_file.txt', 'new_directory/destination_file.txt')
  ```

#### 3. 删除操作

- **`shutil.rmtree(path, ignore_errors=False, onerror=None)`**

  递归删除目录树。请谨慎使用，因为此操作是不可逆的。

  ```python
  import shutil

  shutil.rmtree('directory_to_delete')
  ```

#### 4. 压缩和解压缩操作

- **`shutil.make_archive(base_name, format, root_dir=None, base_dir=None, verbose=0, dry_run=False, owner=None, group=None, logger=None)`**

  创建压缩文件。`format` 可以是 `'zip'`, `'tar'`, `'gztar'`, `'bztar'`, `'xztar'` 等。

  ```python
  import shutil

  shutil.make_archive('archive_name', 'zip', 'directory_to_compress')
  ```

- **`shutil.unpack_archive(filename, extract_dir=None, format=None)`**

  解压缩文件到指定目录。

  ```python
  import shutil

  shutil.unpack_archive('archive_name.zip', 'extract_to_directory')
  ```

#### 5. 磁盘使用情况

- **`shutil.disk_usage(path)`**

  获取指定路径所在磁盘的使用情况。返回一个包含总空间、已用空间和可用空间的命名元组。

  ```python
  import shutil

  usage = shutil.disk_usage('/')
  print(f"Total: {usage.total} bytes")
  print(f"Used: {usage.used} bytes")
  print(f"Free: {usage.free} bytes")
  ```

#### 6. 高级文件操作

- **`shutil.which(cmd, mode=os.F_OK | os.X_OK, path=None)`**

  查找可执行文件的路径，类似于 Unix 中的 `which` 命令。

  ```python
  import shutil

  path = shutil.which('python')
  print(path)  # 输出python可执行文件的路径
  ```

#### 7. 特殊文件操作

- **`shutil.chown(path, user=None, group=None)`**

  更改文件或目录的所有者和组。

  ```python
  import shutil

  shutil.chown('example.txt', user='username', group='groupname')
  ```

#### 8. 文件系统空间操作

- **`shutil.get_archive_formats()`**

  返回支持的归档格式列表。

  ```python
  import shutil

  formats = shutil.get_archive_formats()
  print(formats)
  ```

- **`shutil.register_archive_format(name, function, extra_args=None, description='')`**

  注册新的归档格式。

  ```python
  import shutil

  def my_archive_function(base_name, base_dir, **kwargs):
      # 自定义归档逻辑
      pass

  shutil.register_archive_format('my_format', my_archive_function, description='My custom format')
  ```

- **`shutil.unregister_archive_format(name)`**

  注销已注册的归档格式。

  ```python
  import shutil

  shutil.unregister_archive_format('my_format')
  ```

通过以上这些函数，`shutil` 模块能够帮助我们更加方便、快捷地进行文件和目录的操作。