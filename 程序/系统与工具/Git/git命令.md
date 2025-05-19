好的，这里是一些更详细的 Git 基础命令说明和使用示例。

### 配置 Git

1. **配置全局用户名和邮箱**：
    ```sh
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```
    这些命令设置了提交记录中的用户名和邮箱。

2. **配置特定仓库的用户名和邮箱**：
    ```sh
    git config user.name "Your Name"
    git config user.email "your.email@example.com"
    ```
    这些命令只在当前仓库中设置用户名和邮箱。

3. **查看配置信息**：
    ```sh
    git config --list
    ```
    列出所有 Git 配置，包括全局和仓库级别的设置。

### 初始化和克隆仓库

1. **初始化新的 Git 仓库**：
    ```sh
    git init
    ```
    在当前目录初始化一个新的 Git 仓库。

2. **克隆远程仓库**：
    ```sh
    git clone <repository-url>
    ```
    从指定的 URL 克隆远程仓库到本地。

### 文件操作

1. **查看仓库状态**：
    ```sh
    git status
    ```
    显示工作目录和暂存区的状态。

2. **添加文件到暂存区**：
    ```sh
    git add <file>
    git add .  # 添加所有文件
    ```
    将文件添加到暂存区，准备提交。

3. **提交更改**：
    ```sh
    git commit -m "Commit message"
    ```
    将暂存区的更改提交到本地仓库。

4. **查看提交历史**：
    ```sh
    git log
    ```
    显示提交历史记录。

### 分支操作

1. **查看所有分支**：
    ```sh
    git branch
    ```
    列出本地所有分支，并标记当前所在分支。

2. **创建新分支**：
    ```sh
    git branch <branch-name>
    ```
    创建一个新分支。

3. **切换分支**：
    ```sh
    git checkout <branch-name>
    ```
    切换到指定分支。

4. **创建并切换到新分支**：
    ```sh
    git checkout -b <branch-name>
    ```
    创建新分支并切换到该分支。

5. **删除分支**：
    ```sh
    git branch -d <branch-name>
    ```
    删除本地分支。

### 合并与变基

1. **合并分支**：
    ```sh
    git merge <branch-name>
    ```
    将指定分支合并到当前分支。

2. **变基**：
    ```sh
    git rebase <branch-name>
    ```
    将当前分支的更改应用到目标分支的基础上。

### 远程操作

1. **查看远程仓库**：
    ```sh
    git remote -v
    ```
    列出所有远程仓库及其 URL。

2. **添加远程仓库**：
    ```sh
    git remote add origin <repository-url>
    ```
    添加一个名为 `origin` 的远程仓库。

3. **移除远程仓库**：
    ```sh
    git remote remove <name>
    ```
    移除指定的远程仓库。

4. **拉取远程仓库的更改**：
    ```sh
    git pull
    ```
    从远程仓库拉取并合并更改到当前分支。

5. **推送本地更改到远程仓库**：
    ```sh
    git push origin <branch-name>
    ```
    将指定分支的更改推送到远程仓库。

### 标签操作

1. **创建标签**：
    ```sh
    git tag <tag-name>
    ```
    创建一个标签。

2. **推送标签到远程仓库**：
    ```sh
    git push origin <tag-name>
    ```

3. **查看标签**：
    ```sh
    git tag
    ```

4. **删除标签**：
    ```sh
    git tag -d <tag-name>
    ```

### 撤销操作

1. **撤销工作目录中的更改**：
    ```sh
    git checkout -- <file>
    ```
    撤销对文件的修改。

2. **重置暂存区和工作目录**：
    ```sh
    git reset --hard HEAD
    ```
    将暂存区和工作目录重置为最新提交。

3. **撤销最近的提交但保留更改**：
    ```sh
    git reset --soft HEAD~1
    ```
    将最近的提交回滚，但保留更改在工作目录中。

4. **撤销最近的提交并丢弃更改**：
    ```sh
    git reset --hard HEAD~1
    ```
    将最近的提交回滚，并丢弃所有更改。

### 日常操作示例

1. **创建新仓库并提交**：
    ```sh
    mkdir myproject
    cd myproject
    git init
    echo "Hello, Git" > README.md
    git add README.md
    git commit -m "Initial commit"
    ```

2. **克隆仓库并创建新分支**：
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    git checkout -b feature-branch
    ```

3. **合并分支并推送更改**：
    ```sh
    git checkout main
    git merge feature-branch
    git push origin main
    ```

这些命令覆盖了 Git 的基本操作和常见使用场景，帮助你有效地管理代码仓库。如果你需要更高级的操作或更具体的示例，请告诉我。