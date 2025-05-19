在 Kali Linux 中安装 LAMP（Linux + Apache + MySQL/MariaDB + PHP）环境，可以按照以下步骤进行：

1. **更新系统：**
   ```bash
   sudo apt update
   sudo apt upgrade
   ```

2. **安装 Apache：**
   ```bash
   sudo apt install apache2
   ```

   启动 Apache 并设置其随系统启动：
   ```bash
   sudo systemctl start apache2
   sudo systemctl enable apache2
   ```

   在浏览器中输入 `http://localhost`，你应该能够看到 Apache 的默认欢迎页面。

3. **安装 MySQL 或 MariaDB：**
   选择安装 MySQL 或 MariaDB，以下为 MariaDB 的安装示例：
   ```bash
   sudo apt install mariadb-server
   ```

   启动 MariaDB 并设置其随系统启动：
   ```bash
   sudo systemctl start mariadb
   sudo systemctl enable mariadb
   ```

   运行安全性脚本以提高数据库的安全性：
   ```bash
   sudo mysql_secure_installation
   ```

4. **安装 PHP 及相关模块：**
   ```bash
   sudo apt install php libapache2-mod-php php-mysql
   ```

   重启 Apache 以使 PHP 模块生效：
   ```bash
   sudo systemctl restart apache2
   ```

5. **测试 LAMP 环境：**
   创建一个简单的 PHP 测试文件，例如 `info.php`，并将其放置在 Apache 的 Web 根目录中（通常是 `/var/www/html/`）：
   ```php
   <?php
   phpinfo();
   ?>
   ```

   通过浏览器访问 `http://localhost/info.php`，你应该能够看到 PHP 信息页面。

请注意，这只是一个基本的 LAMP 环境安装。在生产环境中，应该采取额外的安全措施，例如配置防火墙、限制数据库权限等，以确保系统的安全性。