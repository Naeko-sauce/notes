在 `fish` shell 中，`unset` 命令使用不同的语法。你可以使用 `set -e` 来取消环境变量的设置。以下是具体步骤：

### 取消代理设置

1. **取消 HTTP 和 HTTPS 代理设置：**

   ```sh
   set -e http_proxy
   set -e https_proxy
   set -e HTTP_PROXY
   set -e HTTPS_PROXY
   ```

2. **验证取消代理设置：**

   ```sh
   echo $http_proxy
   echo $https_proxy
   ```

   这些命令应该不返回任何内容。

3. **重新尝试克隆仓库：**

   ```sh
   git clone https://github.com/chaozwn/astronvim_with_coc_or_mason ~/.config/nvim
   ```

### 使用临时禁用代理

如果你只想临时禁用代理来克隆仓库，可以使用以下命令：

```sh
env -u http_proxy -u https_proxy git clone https://github.com/chaozwn/astronvim_with_coc_or_mason ~/.config/nvim
```

### 检查代理服务

如果你确实需要使用代理，请确保代理服务在 `127.0.0.1:7890` 上运行并配置正确：

- 检查代理服务状态：确保代理服务已启动并在预期端口上监听。
- 验证代理是否工作：可以尝试通过代理访问其他网站或资源，确认代理服务正常工作。

### 使用 SSH 克隆

如果 HTTPS 方式依旧无法使用，可以尝试使用 SSH 方式克隆：

1. **确保你已经设置了 SSH 密钥，并将公钥添加到 GitHub 上**。

2. **使用 SSH 方式克隆仓库**：

   ```sh
   git clone git@github.com:chaozwn/astronvim_with_coc_or_mason.git ~/.config/nvim
   ```

通过这些步骤，你应该能够成功克隆仓库。如果仍有问题，请检查你的网络连接和代理服务器的配置。