---
title: Hexo + Gihub入坑记
date: 2015-05-10 12:35:48
tags:  hexo github 
---

*注: 整理或折腾自网络, 仅供参考,入坑需谨慎, 不对各种疑问负责*
*如遇到各种bug, 可以卸载node、git,重启pc、重装node、git（注意备份.md文件(文章源文件) .yml文件(相关配置)）*<!--more-->
## 安装window版git  & node.js

下一步,下一步, 默认设置......

**github建仓库, + create  Repository**
建立与你用户名对应的仓库，仓库名必须为【your_user_name.github.io】

**配置SSH-Key-本地git项目与远程的github联系**


首先我们需要检查你电脑上现有的ssh key：
`$ cd ~/. ssh      #检查本机的ssh密钥`
如果提示：No such file or directory 说明你是第一次使用git。

**生成新的SSH Key**
```php
$ ssh-keygen -t rsa -C "邮件地址@youremail.com"```
`Generating public/private rsa key pair.
Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>`
注意1: 此处的邮箱地址，你可以输入自己的邮箱地址；注意2: 此处的「-C」的是大写的「C」

然后系统会要你输入密码：
```php
Enter passphrase (empty for no passphrase):<输入加密串>
Enter same passphrase again:<再次输入加密串>
```
在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。

注意：输入密码的时候没有*字样的，你直接输入就可以了。

**添加SSH Key到GitHub**
在本机设置SSH Key之后，需要添加到GitHub上，以完成SSH链接的设置。
1、打开本地C:\Documents and Settings\Administrator.ssh\id_rsa.pub文件。此文件里面内容为刚才生成人密钥。如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。

2、登陆github系统。点击右上角的 Account Settings--->SSH Public keys ---> add another public keys

3、把你本地生成的密钥复制到里面（key文本框中）， 点击 add key 就ok了

**测试**
可以输入下面的命令，看看设置是否成功，git@github.com的部分不要修改：
`$ ssh -T git@github.com`
成功提示
`Hi cnfeat! You've successfully authenticated, but GitHub does not provide shell access.`

**设置用户信息**
现在你已经可以通过SSH链接到GitHub了，还有一些个人信息需要完善的。
Git会根据用户的名字和邮箱来记录提交。GitHub也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的
```php
$ git config --global user.name "你的用户名"//用户名
$ git config --global user.email  "你的邮箱@gmail.com"//填写自己的邮箱
```

------------

## 安装hexo
- Node安装
Node可以去官网下载，或是在国内下载，由于众所周知的原因，这里放一个nodejs.cn的链接
Node内置npm包，我们之后就可以打开node命令行使用npm进行安装一些依赖，如果觉得太慢，可以使用淘宝镜像cnpm

- Hexo安装
好的，现在我们Node,git,github都弄好了，现在可以本地化一个hexo了, 在D盘新建hexo文件夹, 打开Git命令行，执行如下命令(淘宝免屏蔽链接)
`$ npm install -g cnpm --registry=https://registry.npm.taobao.org`
npm没反映,大天朝,你懂得,各种墙,还好有taobao这样的良心企业,给npm做了镜像,去安装一个 cnpm 用它来代替大部分的 npm

git再运行指令
```php
 hexo init
 npm install -g hexo-cli
```
- 换博客主题, 例如某网友提供的一主题
```php
git clone https://github.com/MOxFIVE/hexo-theme-yelee.git themes/yelee
```
- 配置
修改hexo根目录下的 _config.yml ： theme:    yelee    , 注意yelee前面留一个空格

- 更新
```php
cd themes/yilia
git pull
```
- 在本地浏览器预览
```php
hexo generate       #自动根据当前目录下文件,生成静态页面至public目录
hexo server         #运行本地服务
```
按ctrl+c停止
`(node:24064) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
`
浏览器输入http://localhost:4000就可以看到效果。(4000端口若被占用, 杀进程)
- hexo目录说明
```php
├── .deploy_git       #需要部署的文件,会传到github上
├── node_modules  #Hexo插件
├── public        #生成的静态网页文件
├── scaffolds     #模板
├── source        #博客正文和其他源文件, 404 favicon CNAME 等都应该放在这里
|   ├── _drafts   #草稿
|   └── _posts    #文章
├── themes        #主题
├── _config.yml   #全局配置文件
└── package.json
```
- 添加博文
`hexo new "postName" #新建博文,其中postName是博文题目`
 源文件在hexo\source\_posts 目录下.md文件
如果不想博文在首页全部显示, 并能出现阅读全文按钮效果, 需要在你想在首页显示的部分下添加
`<!--more-->`
这点和wordpress是一样的
## 发布到github上
发布到github,是需要安装一下的

`$ npm install hexo-deployer-git --save`
根目录文件_config.yml先设置, 注意冒号之后留一个空格
```php
deploy:
  type:   git
  repo:   https://github.com/it80/it80.github.io.git
  branch:  master
```
先`hexo clean  #清除缓存`, 再`hexo g  #生成静态页面` 再`hexo d #将文章部署到Github`


- **不完全参考(敬请谷歌一下)** 

HEXO 趟坑笔记  http://www.jianshu.com/p/31eb84182156

手把手教你使用Hexo + Github Pages搭建个人独立博客https://segmentfault.com/a/1190000004947261

MOxFIVE 将 Hexo 博客部署到 GitHub Pages
http://moxfive.xyz/2015/11/04/hexo-deployment/

手把手教 GitHub + Hexo 搭建博客
http://www.jianshu.com/p/ab21abc31153

Mac上搭建基于GitHub Page的Hexo博客
http://jeasonstudio.github.io/2016/05/26/Mac%E4%B8%8A%E6%90%AD%E5%BB%BA%E5%9F%BA%E4%BA%8EGitHub-Page%E7%9A%84Hexo%E5%8D%9A%E5%AE%A2/#创建仓库

hexo常用命令笔记
https://segmentfault.com/a/1190000002632530