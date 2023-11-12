CentOS 是一个流行的 Linux 发行版，它基于 Red Hat Enterprise Linux（RHEL）构建。以下是一些 CentOS 中常用的命令以及它们的简要使用方法：

**1. `ls` - 列出文件和目录：**

- `ls`：列出当前目录中的文件和目录。
- `ls -l`：以长格式列出文件和目录，包括详细信息（权限、所有者、大小等）。
- `ls -a`：显示所有文件，包括隐藏文件（以`.`开头的文件）。

**2. `cd` - 切换目录：**

- `cd directory_name`：进入名为 `directory_name` 的目录。
- `cd ..`：返回上一级目录。
- `cd ~`：切换到当前用户的主目录。

**3. `pwd` - 显示当前工作目录：**

- `pwd`：显示当前所在的目录的完整路径。

**4. `mkdir` - 创建目录：**

- `mkdir directory_name`：创建名为 `directory_name` 的新目录。

**5. `rmdir` - 删除目录：**

- `rmdir directory_name`：删除名为 `directory_name` 的空目录。

**6. `rm` - 删除文件或目录：**

- `rm file_name`：删除名为 `file_name` 的文件。
- `rm -r directory_name`：递归删除名为 `directory_name` 的目录及其内容。

**7. `cp` - 复制文件和目录：**

- `cp source_file destination`：将 `source_file` 复制到 `destination`。
- `cp -r source_directory destination`：递归复制整个目录。

**8. `mv` - 移动文件和目录或重命名：**

- `mv source destination`：将 `source` 移动到 `destination`。
- `mv old_name new_name`：重命名文件或目录。

**9. `touch` - 创建空文件：**

- `touch file_name`：创建一个名为 `file_name` 的空文件。

**10. `cat` - 查看文件内容：** - `cat file_name`：显示文件 `file_name` 的内容。

**11. `more` 和 `less` - 逐页查看文件内容：** - `more file_name`：逐页显示文件内容，按空格键翻页。 - `less file_name`：逐页显示文件内容，使用箭头键和空格键进行导航。

**12. `head` 和 `tail` - 查看文件开头和结尾：** - `head file_name`：显示文件的开头部分。 - `tail file_name`：显示文件的末尾部分。

**13. `grep` - 文本搜索：** - `grep search_term file_name`：在文件 `file_name` 中搜索包含 `search_term` 的行。

**14. `ps` - 查看进程：** - `ps`：显示当前用户的运行进程。 - `ps aux`：显示所有用户的运行进程。

**15. `kill` - 终止进程：** - `kill process_id`：终止具有给定进程 ID 的进程。

**16. `top` - 查看系统资源使用情况：** - `top`：显示实时的系统性能和进程信息。

这些是一些在 CentOS 中常用的基本命令。要深入了解每个命令的详细用法和选项，请查阅命令的手册页（例如，`man ls` 可以查看 `ls` 命令的手册页）。此外，还可以使用 `--help` 选项来获取命令的简要帮助，例如，`ls --help`。