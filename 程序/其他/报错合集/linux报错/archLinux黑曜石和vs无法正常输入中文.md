一般而言，对于 AUR 安装的 VSCode 默认启用了 Wayland 支持，而 fcitx 5 在纯 Wayland 模式下输入法支持不稳定，尤其在 Electron 应用中表现更差。

所以我们需要确定原因:
✅ 精确解决方案（针对你的情况）：
✅ 方法一：强制 VSCode 使用 XWayland 运行（成功率最高）
打开终端，输入以下命令来测试是否能输入中文：

```bash
env GTK_IM_MODULE=fcitx QT_IM_MODULE=fcitx XMODIFIERS="@im=fcitx" code --ozone-platform=x11
```
如果此命令下能输入中文，说明就是 Electron + Wayland 的锅。

此外我试过，并没有任何方法能够一劳永逸的解决这个问题，只有在每个软件启动的时候加上
如下配置:

✅ 更稳妥有效的终极方案：为 VSCode 等 Electron 应用单独设置启动方式
你可以为 VSCode 设置专属 desktop 启动文件，显式传入环境变量，确保 Electron 程序在 x 11 下运行：

✅ 步骤如下（适用于任何 Electron 程序）：
打开终端：

```bash
cp /usr/share/applications/code.desktop ~/.local/share/applications/code-x11.desktop
```

编辑这个新文件：

```bash
nano ~/.local/share/applications/code-x11.desktop
```
找到 `Exec=` 那一行，改成：

```ini
Exec=env ELECTRON_OZONE_PLATFORM_HINT=x11 code --no-sandbox --unity-launch %F
```
其中要确保: 你的 VSCode 是该路径 `/usr/share/applications/code.desktop`, 并且确保你的 Hyprland 使用的是: `~/.local/share/applications/` 此路径进行展示应用

---
上述为 VSCode，Obsidian 也是同理，不过 Obsidian 因为我是 AppImage 以及 AppImageLauncher 的方式进行启动所以:

我的方法为:
✅ 方法一：修改 Obsidian 的 .desktop 文件（推荐）
你已经用 AppImageLauncher 启动过 Obsidian，那它应该已自动生成 .desktop 文件，路径如下：

```ruby
~/.local/share/applications/appimagekit-obsidian.desktop
```
步骤：
编辑该文件：

```bash
nano ~/.local/share/applications/appimagekit-obsidian.desktop
```
找到这一行：

```ini
Exec=/path/to/Obsidian.AppImage
```

改为：

```bash
Exec=env ELECTRON_OZONE_PLATFORM_HINT=x11 /path/to/Obsidian.AppImage
```

保存并退出，然后重新打开 Obsidian，测试中文输入法。

✅ 优点：只需操作一次即可，不依赖 Hyprland 配置，全局适配 Electron 环境。

✅ 方法二：修改 AppImageLauncher 的集成行为（进阶）
AppImageLauncher 实际调用 `/usr/bin/appimagelauncher` 来处理 .AppImage 文件。

要对其所有通过 AppImageLauncher 启动的 AppImage 应用统一设置环境变量，可创建一个 wrapper 脚本。

步骤（高级用户推荐）：
创建一个新的 wrapper 脚本：

```bash
sudo mv /usr/bin/appimagelauncher /usr/bin/appimagelauncher.real
sudo nano /usr/bin/appimagelauncher
```
输入以下内容：

```bash
#!/bin/bash
export ELECTRON_OZONE_PLATFORM_HINT=x11
exec /usr/bin/appimagelauncher.real "$@"
```

保存并退出，然后：

```bash
sudo chmod +x /usr/bin/appimagelauncher
```

这个方法可以对所有通过 AppImageLauncher 启动的 Electron 应用统一设置 x 11 平台。