要使用 Git 连接到 GitHub，可以使用 HTTPS 或 SSH 两种方式。以下是详细步骤：

### 通过 HTTPS 连接 GitHub

1. **生成 GitHub 访问令牌（Personal Access Token, PAT）**：
    - 访问 GitHub 的[设置页面](https://github.com/settings/tokens)。
    - 点击 "Generate new token"。
    - 为令牌命名，选择所需的权限，然后生成令牌并保存。

2. **配置 Git 用户名和邮箱**：
    ```sh
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

3. **克隆 GitHub 仓库**：
    ```sh
    git clone https://github.com/username/repository.git
    ```
    当 Git 提示输入用户名和密码时，输入你的 GitHub 用户名和生成的访问令牌。

### 通过 SSH 连接 GitHub

1. **生成 SSH 密钥**：
    - 打开终端，运行以下命令来生成新的 SSH 密钥（替换 email@example.com 为你的 GitHub 邮箱）：
      ```sh
      ssh-keygen -t rsa -b 4096 -C "email@example.com"
      ```
    - 当提示输入保存位置时，按 Enter 键使用默认位置（`~/.ssh/id_rsa`）。
    - 设置一个安全密码（可选）。

2. **添加 SSH 密钥到 SSH 代理**：
    - 启动 SSH 代理：
      ```sh
      eval "$(ssh-agent -s)"
      ```
    - 将 SSH 密钥添加到代理：
      ```sh
      ssh-add ~/.ssh/id_rsa
      ```

3. **将 SSH 公钥添加到 GitHub**：
    - 复制 SSH 公钥到剪贴板：
      ```sh
      cat ~/.ssh/id_rsa.pub
      ```
    - 打开 GitHub，进入 [SSH 和 GPG 密钥设置页面](https://github.com/settings/keys)。
    - 点击 "New SSH key" 按钮，粘贴公钥并保存。

4. **克隆 GitHub 仓库**：
    ```sh
    git clone git@github.com:username/repository.git
    ```

### 常见问题和解决方法

1. **验证 SSH 连接**：
    ```sh
    ssh -T git@github.com
    ```
    你应该看到类似 "Hi username! You've successfully authenticated, but GitHub does not provide shell access." 的消息。

2. **更新已克隆仓库的远程 URL**：
    如果你已经通过 HTTPS 克隆了仓库，并希望改为 SSH，可以使用以下命令：
    ```sh
    git remote set-url origin git@github.com:username/repository.git
    ```

3. **检查配置和连接问题**：
    - 确保你已正确配置 Git 用户名和邮箱。
    - 确保你的网络连接正常，代理设置正确（如有需要）。
    - 检查防火墙和安全软件是否阻止了 Git 连接。

通过这些步骤，你应该能够成功使用 Git 连接到 GitHub，并管理你的代码仓库。如果遇到其他问题，请提供详细错误信息，以便进一步排查。