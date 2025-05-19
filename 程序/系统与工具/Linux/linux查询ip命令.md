在CentOS中，你可以使用多种命令来查询IP地址和网络配置信息。以下是一些常用的命令：

1. **`ifconfig` 命令**：`ifconfig` 命令用于显示和配置网络接口的信息，包括IP地址。要查看所有网络接口的信息，打开终端并运行以下命令：
    
    bashCopy code
    
    `ifconfig`
    
    这将显示每个网络接口的详细信息，包括IP地址。
    
2. **`ip addr` 命令**：`ip addr` 命令也用于显示网络接口的信息，包括IP地址。运行以下命令：
    
    bashCopy code
    
    `ip addr`
    
    这将显示网络接口及其对应的IP地址。
    
3. **`hostname -I` 命令**：`hostname` 命令用于查看主机名，而 `-I` 选项用于显示主机的IP地址。运行以下命令：
    
    bashCopy code
    
    `hostname -I`
    
    这将显示主机的IP地址列表。
    
4. **`nmcli` 命令**：`nmcli` 是NetworkManager命令行工具，可用于管理网络连接和查看IP地址。要查看活动连接的IP地址，运行以下命令：
    
    bashCopy code
    
    `nmcli connection show`
    
    这将列出所有活动连接以及它们的IP地址。
    
5. **`curl` 命令**：`curl` 命令通常用于从网络上获取数据，但也可以用于查询公共IP地址。运行以下命令：
    
    bashCopy code
    
    `curl ifconfig.me`
    
    这将返回你的公共IP地址。
    

这些命令中的任何一个都可以用于查询CentOS系统上的IP地址和网络配置信息。选择其中一个命令，具体取决于你的需求和偏好。