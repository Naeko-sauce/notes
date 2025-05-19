要在 Kali Linux 中卸载 LAMP（Linux + Apache + MySQL/MariaDB + PHP）环境，可以按照以下步骤进行：

1. **卸载 Apache：**
   ```bash
   sudo apt remove apache2
   sudo apt autoremove
   ```

   这将删除 Apache 2 软件包以及可能不再需要的相关依赖项。

2. **卸载 MySQL 或 MariaDB：**
   如果你使用的是 MySQL：
   ```bash
   sudo apt remove mysql-server
   sudo apt autoremove
   ```

   或者如果你使用的是 MariaDB：
   ```bash
   sudo apt remove mariadb-server
   sudo apt autoremove
   ```

3. **卸载 PHP 及相关模块：**
   ```bash
   sudo apt remove php libapache2-mod-php php-mysql
   sudo apt autoremove
   ```

4. **删除 Apache 和 MariaDB（如果需要）的配置文件：**
   ```bash
   sudo rm -r /etc/apache2
   ```

   如果你使用的是 MariaDB：
   ```bash
   sudo rm -r /etc/mysql
   ```

5. **删除网站文件（可选）：**
   如果你在 `/var/www/html/` 或其他目录中有网站文件，可以选择删除它们：
   ```bash
   sudo rm -r /var/www/html/*
   ```

6. **清理系统：**
   ```bash
   sudo apt autoclean
   ```

   这将清理 apt 缓存中的不再需要的软件包。

请注意，在执行这些步骤之前，请确保你真的希望完全删除 LAMP 环境。一旦卸载，相关的配置文件和数据将被删除。确保备份任何重要的数据和配置文件，以防发生意外。