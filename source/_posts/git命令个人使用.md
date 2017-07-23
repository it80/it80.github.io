---
title: git命令个人使用
date: 2017-01-10
tags:  git 
---

**本地git目录删除文件**

    git rm test.txt
命令行提示信息rm 'test.txt'
<!--more-->
**确认删除**
    git commit -m "remove test"

命令行提示信息 
```
[master eb2687e] rm test
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 test.txt
```
 
**将本地仓库中的数据推送到远程仓库**

    git push

提示信息
```
Counting objects: 2, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 215 bytes | 0 bytes/s, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To 1024china.github.com:1024china/1024.git
   0b4a48b..eb2687e  master -> master
```
远程git仓库上**手动操作**删除内容后，需要在本地同步看到变化
本地命令行执行` git pull`  命令抓取数据合并到本地

更多>>Git-基础-远程仓库的使用
 https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84%E4%BD%BF%E7%94%A8