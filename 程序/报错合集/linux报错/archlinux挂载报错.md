```
访问“新加卷”时发生错误，系统返回信息：请求的操作已失败: Error mounting /dev/sda 2 at /run/media/naiko/新加卷: wrong fs type, bad option, bad superblock on /dev/sda 2, missing codepage or helper program, or other error
```
### 解决方法
*   先输入 `sudo fdisk -l` 找到要挂载的硬盘位置
* 然后使用 `sudo mkdir -p /run/media/naiko/新加卷` 创建挂载点
* 然后使用 `sudo mount -t ntfs /dev/sda2  /run/media/naiko/新加卷` 尝试挂载。/dev/sda2 是硬盘的路径