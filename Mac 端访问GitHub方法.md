# Mac 端访问GitHub方法

通过配置host文件直接访问GitHub的服务器，绕过域名解析。

1. 解析GitHub的IP地址

   1. 通过 https://www.ipaddress.com/ 获取 github.com 和 github.global.ssl.fastly.net 的ip地址。

   2. 我于2022年2月23日17时35分获取的IP地址

      ```
      # GitHub的IP地址
      github.com 140.82.112.3
      github.global.ssl.fastly.net 199.232.69.194
      ```

2. 向电脑的host文件末尾添加搜索出的IP地址

   - windows

     1. 打开文件：C:/windows/system32/drivers/etc/hosts
     2. 把两个ip地址复制到末尾
     3. 打开终端（快捷键 win+x 选择C），运行：ipconfig /flushdns，更新host文件

   - Mac

     1. 打开文件：/etc/hosts（使用vi命令有效：sudo vi /etc/hosts）

     2. 输入英文状态的 **i** 可进行编辑，把两个ip地址复制到末尾，点击Esc并输入

        ```
        :wq!
        ```

        推出编辑器

     3. 打开终端（通过聚焦搜索-搜索“终端”），运行

        ```
        sudo killall -HUP mDNSResponder
        ```

        更新host文件

   - Linux

     1. 打开文件：/etc/hosts
     2. 把两个ip地址复制到末尾
     3. 打开终端，运行：systemctl restart nscd对host文件进行更行

