看起来你当前的 Git 远程仓库 URL 仍然是 HTTPS 而不是 SSH，这就是为什么你在推送时仍然被要求输入用户名和密码。你需要将远程仓库的 URL 更改为使用 SSH。

### 更改远程仓库 URL 到 SSH

1. **检查当前远程仓库 URL**：

    ```sh
    git remote -v
    ```

    你会看到类似下面的输出：

    ```sh
    origin  https://github.com/Naeko-sauce/notes.git (fetch)
    origin  https://github.com/Naeko-sauce/notes.git (push)
    ```

2. **将远程仓库 URL 更改为 SSH**：

    使用以下命令将远程仓库 URL 从 HTTPS 更改为 SSH：

    ```sh
    git remote set-url origin git@github.com:Naeko-sauce/notes.git
    ```

3. **再次检查远程仓库 URL**：

    确认 URL 已更改：

    ```sh
    git remote -v
    ```

    你应该看到类似下面的输出：

    ```sh
    origin  git@github.com:Naeko-sauce/notes.git (fetch)
    origin  git@github.com:Naeko-sauce/notes.git (push)
    ```

4. **推送代码到 GitHub**：

    现在，你可以推送代码到 GitHub：

    ```sh
    git push origin main
    ```

### 示例

```sh
╭─naiko@naiko in repo: notes on  main [!⇡1] took 2ms
╰─λ git remote -v
origin  https://github.com/Naeko-sauce/notes.git (fetch)
origin  https://github.com/Naeko-sauce/notes.git (push)

╭─naiko@naiko in repo: notes on  main [!⇡1] took 2ms
╰─λ git remote set-url origin git@github.com:Naeko-sauce/notes.git

╭─naiko@naiko in repo: notes on  main [!⇡1] took 2ms
╰─λ git remote -v
origin  git@github.com:Naeko-sauce/notes.git (fetch)
origin  git@github.com:Naeko-sauce/notes.git (push)

╭─naiko@naiko in repo: notes on  main [!⇡1] took 2ms
╰─λ git push origin main
```

这样，你的更改就会被推送到 GitHub 仓库中，并且你不会再被要求输入用户名和密码。如果仍有问题，请告诉我，我会继续帮助你解决。