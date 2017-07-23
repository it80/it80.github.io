---
title: git相关命令
date: 2015-05-09
tags: git
---

**第一步:**   **github.com**  上添加新仓库 &quot;Create New Repository&quot;

　　 **第二步:**  本地关联远程库.添加后，远程库的名字就是  **origin** ，这是  **Git**  默认的叫法，也可以改成别的，但是  **origin**  这个名字一看就知道是远程库。
　　　 **git remote add origin****  **[**https://github.com/Durant35/[Repository**](https://github.com/Durant35/%5BRepository)** ****Name].git**
<!--more-->
　　把本地库的内容推送到远程，用  **git push**  命令，实际上是把当前分支  **master**  推送到远程。
　　由于远程库是空的，我们第一次推送  **master**  分支时，加上了  **-u**  参数， **Git**  不但会把本地的  **master**  分支内容推送的远程新的  **master**  分支，还会把本地的  **master**  分支和远程的  **master**  分支关联起来，在以后的推送或者拉取时就可以简化命令。
　　　 **git push -u origin master**

　　把本地  **master**  分支的最新修改推送至  **GitHub** ！
　　　 **git push origin master**

　　 **第三步：**  查看改变
　　查看本地文件夹改变
　　　 **git status**

　　 **第四步:**  文件/文件夹创建、编写
　　　 **git add file-name** 　　　　# 创建
　　　 **git rm file-name** 　　　　# 删除
　　　 **git add .** 　　　　　　　　# git add all files changed

　　 **第五步:**  先本地提交，后远程提交
　　　 **git commit -m &quot;messages&quot;**
　　　 **git push origin master**

　　 **第六步:**   **git**  版本回退
　　　(注意  **hard**  前面是两个 **&quot;**** -&quot;**)
　　　 **git reset –hard commit\_id**

　　1)  **HEAD**  指向的版本就是当前版本
　　2)  **commit\_id**  通过以下命令获取
　　　 **git log** 　　　查看提交历史 –&gt; 回退到过去哪个版本
　　　 **git reflog** 　　查看命令历史 –&gt; 回到未来的哪个版本

### **git****  高级进阶**

- .查看本地文件改变
　 **git diff &quot;file name&quot;**
- .查看本地与远程库区别
　 **git diff master origin**
- .重写commit 信息（如日志信息）
　　　(注意  **amend**  前面是两个 **&quot;**** -&quot;**)
　 **git commit –amend**
- .从跟踪清单中删除（想把文件从Git 仓库中删除（亦即从暂存区域移除），但仍然希望保留在当前工作目录中）
　**git rm –cache (folder-name/. or file-name)​​​​**
- .移出暂存区（绿变红）
　 **git reset HEAD file-name**

### **git****  分支**

- .删除分支
　 **git branch -d branch-name**
- .强制删除分支
　 **git branch -D branch-name**


转自 http://durant35.github.io/2016/07/26/tool_git%E5%87%A0%E6%AD%A5%E8%B5%B0/