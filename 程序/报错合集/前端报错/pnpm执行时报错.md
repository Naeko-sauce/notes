```
PS D:\len\wrxxy\bolg> pnpm create valaxy pnpm : 无法加载文件 C:\Program Files\nodejs\pnpm.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170 中的 about_Execution_Pol icies。所在位置行: 1 字符: 1 + pnpm create valaxy + ~~~~ + CategoryInfo : SecurityError: (:) []，PSSecurityException + FullyQualifiedErrorId : UnauthorizedAccess PS D:\len\wrxxy\bolg>
```
# 解决方法
看起来您遇到了 PowerShell 脚本执行策略的问题。默认情况下，Windows 上的 PowerShell 有一个执行策略，以防止运行未签名的脚本。您可以尝试使用以下步骤来解决这个问题：

1. **修改执行策略：** 打开 PowerShell 作为管理员，并运行以下命令修改执行策略：
    ```bash
    Set-ExecutionPolicy RemoteSigned
    ```

    您可能需要确认更改，输入 `Y` 然后按 Enter。

    如果上述命令不起作用，您可以尝试使用以下命令：
    ```bash
    Set-ExecutionPolicy Unrestricted
    ```

    这会允许在您的系统上运行任何脚本，但请注意这样做可能会带来一些安全风险。

2. **重新运行 pnpm 命令：** 在设置了更宽松的执行策略后，尝试重新运行您的 `pnpm create valaxy` 命令。

请注意，执行策略的修改可能会影响系统的安全性，因此请谨慎操作。完成操作后，您可以使用 `Set-ExecutionPolicy` 命令将执行策略设置回默认值，如：
```bash
Set-ExecutionPolicy Restricted
```

如果您的系统受到组策略的控制，可能需要联系系统管理员来进行相应的更改。