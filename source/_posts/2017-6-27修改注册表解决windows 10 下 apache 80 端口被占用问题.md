---
title: windows 10 下 apache 80 端口被占用问题(修改注册表解决)
date: 2016-1-1
tag: php 
---
` netstat -ano  `查看端口占用 

80端口被PID为4的System进程占用。这时候千万不要尝试终结此进程，会蓝屏!<!--more-->

######  网上找到的解除System进程对80端口占用的方法：

- 打开注册表，在cmd下输入：`regedit`。

- 找到：`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\HTTP`。

- 在右边找到`Start`这一项，将其改为0。

- 重启系统，System进程不会占用80端口。


From http://www.imooc.com/article/4423