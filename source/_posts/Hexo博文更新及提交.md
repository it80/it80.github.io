---
title: Hexo博客文章更新及提交
date: 2015-05-11 12:35:48
tags: hexo 
---
====================================================
.deploy_git 目录下打开git Bash命令
查看it80是否有权限登陆
```
$ ssh -T  git@it80.github.com
```
提示
```
Hi it80! You've successfully authenticated, but GitHub does not provide shell access.
```
<!--more-->
设置Git的user name和email(本地有两个账号,所有省略global)：


```
$ git config user.name "it80"
$ git config  user.email "it80@qq.com"（换成你的邮箱地址）
$ hexo g   #生成
$ hexo s   #生成文件在本地查看
$ hexo d   #上传
```

(删除./deploy_git 重新生成用 git init,
将本地仓库和远程仓库连接（这一步骤可以不做）：
$ git remote add origin git@github.com:your_github_user_name/your_github_user_name.github.io.git(远程仓库ssh地址) )
====================================================
Settings - Emails 不勾选 Keep my email address private
更新文章: 命令行进入 hexo  目录下\.deploy_git 
hexo g
hexo d

Hexo建立文章及提交文章命令行提示
- **hexo g**    //生成页面

```
Administrator@XXXXX  MINGW64 /d/hexo
$ hexo g
(node:8852) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Start processing
heINFO  Files loaded in 1.33 s
INFO  Generated: about/index.html
INFO  Generated: archives/2015/05/index.html
INFO  Generated: archives/2015/index.html
INFO  Generated: archives/2015/01/index.html
INFO  Generated: index.html
INFO  Generated: 2015/05/10/Hexo +github/index.html
INFO  Generated: archives/index.html
INFO  Generated: 2015/05/09/about/index.html
INFO  Generated: 2015/01/05/hello-world/index.html
INFO  Generated: background/bg-2.jpg
INFO  Generated: background/bg-1.jpg
INFO  Generated: background/bg-3.jpg
INFO  Generated: img/CSDN.png
INFO  Generated: apple-touch-icon.png
INFO  Generated: img/Coding.png
INFO  Generated: img/LOFTER.png
INFO  Generated: img/Quora.png
INFO  Generated: img/Plunker.png
INFO  Generated: img/SegmentFault.png
INFO  Generated: background/bg-4.jpg
INFO  Generated: img/avatar.png
INFO  Generated: img/V2EX.png
INFO  Generated: img/TiddlyWiki.png
INFO  Generated: img/bilibili.png
INFO  Generated: img/AcFun.png
INFO  Generated: img/niconico.png
INFO  Generated: img/博客园.png
INFO  Generated: img/scrollbar_arrow.png
INFO  Generated: img/知乎.png
INFO  Generated: img/新浪微博.png
INFO  Generated: img/简书.png
INFO  Generated: img/网易云音乐.png
INFO  Generated: img/虾米音乐.png
INFO  Generated: background/backup/bg-2.jpg
INFO  Generated: background/backup/bg-1.jpg
INFO  Generated: img/豆瓣.png
INFO  Generated: background/backup/bg-3.jpg
INFO  Generated: background/backup/bg-4.jpg
INFO  Generated: background/bg-6.jpg
INFO  Generated: background/bg-5.jpg
INFO  Generated: js/main.js
INFO  Generated: js/pc.js
INFO  Generated: js/GithubRepoWidget.js
INFO  Generated: js/toc.js
INFO  Generated: js/search.js
INFO  Generated: js/mobile.js
INFO  Generated: js/instagram.js
INFO  Generated: css/style.css
INFO  48 files generated in 3.89 s
```
- **hexo d**        //部署到github
```
Administrator@XXXXXX  MINGW64 /d/hexo
$ hexo d
(node:26368) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
warning: LF will be replaced by CRLF in 2015/01/05/hello-world/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in 2015/05/09/about/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in 2015/05/10/Hexo +github/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in 2017/06/10/about/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in 2017/06/10/标题/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in about/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2015/01/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2015/05/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2015/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2017/06/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2017/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in css/style.css.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/GithubRepoWidget.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/instagram.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/main.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/mobile.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/pc.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/search.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/toc.js.
The file will have its original line endings in your working directory.
[master 07e344f] Site updated: 2017-06-10 15:38:33
 2 files changed, 7 insertions(+), 7 deletions(-)
Branch master set up to track remote branch master from https://github.com/it80/it80.github.io.git.
To https://github.com/it80/it80.github.io.git
   d637c8d..07e344f  HEAD -> master
INFO  Deploy done: git
```