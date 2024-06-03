由于你使用的是 `fish` shell，我们需要将 `nvim` 的路径添加到 `fish` 的环境变量配置中。以下是具体步骤：

### 步骤：

1. **找到 Neovim 可执行文件的路径：**

   根据你的描述，Neovim 可执行文件在 `~/nvim-linux64/bin` 目录下。

2. **打开 `fish` 配置文件：**

   打开 `~/.config/fish/config.fish` 文件进行编辑。

   ```sh
   nano ~/.config/fish/config.fish
   ```

3. **添加路径到 `PATH` 环境变量：**

   在文件末尾添加以下行，将 `/home/naiko/nvim-linux64/bin` 替换为你的实际路径：

   ```sh
   set -Ux fish_user_paths /home/naiko/nvim-linux64/bin $fish_user_paths
   ```

4. **保存文件并使配置生效：**

   保存文件并退出编辑器，然后运行以下命令以使更改生效：

   ```sh
   source ~/.config/fish/config.fish
   ```

### 验证：

运行以下命令以验证 `nvim` 是否可以全局访问：

```sh
nvim --version
```

如果你看到 Neovim 的版本信息，说明设置成功。

### 额外检查：

如果上述步骤没有解决问题，请确保路径拼写正确，并尝试重启终端或执行以下命令来重新启动 `fish` shell：

```sh
exec fish
```

这样可以确保所有配置都已加载。