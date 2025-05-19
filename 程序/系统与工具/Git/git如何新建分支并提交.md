当然！这里是一个总结，包括如何新建分支、切换分支、以及提交更改到远程仓库的所有步骤：

### 1. **查看现有分支**
   首先，你可以查看本地和远程的分支列表，以确认你当前的分支和远程仓库中的分支。

   ```bash
   # 查看本地分支
   git branch
   
   # 查看远程分支
   git branch -r
   ```

### 2. **创建新分支**
   使用 `git switch -c` 命令（或 `git checkout -b`，旧命令）来创建一个新的分支并切换到该分支。

   ```bash
   # 创建并切换到新分支
   git switch -c <new-branch-name>
   
   # 或者
   git checkout -b <new-branch-name>
   ```

### 3. **查看当前分支**
   确保你在正确的分支上。

   ```bash
   git branch
   ```

### 4. **添加更改**
   将文件更改添加到暂存区。这些更改准备好之后可以提交。

   ```bash
   # 添加所有更改
   git add .
   
   # 或者添加特定文件
   git add <filename>
   ```

### 5. **提交更改**
   提交暂存区的更改，并附上描述性的信息。

   ```bash
   git commit -m "你的提交信息"
   ```

### 6. **推送到远程仓库**
   将本地分支的更改推送到远程仓库。首次推送到新分支时，使用 `-u` 标志来设置跟踪关系。

   ```bash
   # 推送更改到远程仓库的分支
   git push origin <branch-name>
   
   # 如果是新分支并且需要设置上游分支
   git push -u origin <branch-name>
   ```

### 示例
假设你要在名为 `feature-branch` 的新分支上进行开发，流程如下：

1. 查看现有分支：
   ```bash
   git branch -r
   ```

2. 创建并切换到新分支：
   ```bash
   git switch -c feature-branch
   ```

3. 查看当前分支确认切换：
   ```bash
   git branch
   ```

4. 添加更改：
   ```bash
   git add .
   ```

5. 提交更改：
   ```bash
   git commit -m "Add new feature"
   ```

6. 推送到远程仓库：
   ```bash
   git push -u origin feature-branch
   ```

这样，你就完成了从新建分支到推送更改的整个过程。如果有任何问题，随时告诉我！