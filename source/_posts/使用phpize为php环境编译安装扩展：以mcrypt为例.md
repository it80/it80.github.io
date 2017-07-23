---
title: 使用phpize为php环境编译安装扩展：以mcrypt为例, centos环境
date: 2017-05-10 12:35:48
tags:  php 
---
使用phpize为php环境编译安装扩展：以mcrypt为例, centos环境

###### 注:  使用php mcrypt 前必须先安装Libmcrypt
##### 使用php mcrypt 前必须先安装Libmcrypt
<!--more-->
`cd /usr/local/src`

`wget https://jaist.dl.sourceforge.net/project/mcrypt/Libmcrypt/2.5.8/libmcrypt-2.5.8.tar.gz`

`tar -zxvf libmcrypt-2.5.8.tar.gz`

`cd /usr/local/src/libmcrypt-2.5.8`

`./configure --prefix=/usr/local`

`make`

`make install`

------------


------------


1.首先需要确认当前服务器环境php版本。在终端下执行 php -v  （如果php不在path目录下，需要进入到php程序目录）。

获取到对应的版本号以后在这里（[http://php.net/releases/](http://php.net/releases/ "http://php.net/releases/")）找到对应的php版本源码下载地址。

比如我的是php5.3.3 ,对应的下载地址为http://museum.php.net/php5/php-5.3.3.tar.gz,进入工作目录（因为用完即删，我习惯放在tmp目录下）后

`wget http://museum.php.net/php5/php-5.3.3.tar.gz`

将该源码文件下载后解压。

`tar xzvf php-5.4.12.tar.gz`

- 进入扩展目录


在安装一些程序的时候可能有下面的错误。

sh: phpize: command not found

这时候运行` yum install php-devel `安装 php 开发程序即可。


- 进入扩展目录
`cd php-5.4.12/ext`
挑选自己需要安装的扩展进入，比如我需要安装mcrypt

 
```php
cd php-7.1.0/ext/mcrypt/   
phpize 
./configure
 make
 make install
```
执行成功会返回安装so的文件路径。
在php.ini 中添加 扩展引用extension=mcrypt.so即可




