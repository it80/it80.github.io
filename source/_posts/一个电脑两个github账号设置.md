---
title: 一个电脑绑定两个github账号
date: 2015-05-10 12:35:48
tags:  github 
---

**生成秘钥,名称要不同**

    cd ~/.ssh
    ssh-keygen -t rsa -C "XX-1@gmail.com"
    ssh-keygen -t rsa -C "xx-2@gmail.com"
<!--more-->
**添加秘钥到SSH agent, ssh agent默认只读取id_rsa，为了让SSH识别新的私钥，需将其添加到SSH agent中**
防止出错,先`ssh-agent bash`

    ssh-add -k  ~/.ssh/xx-1
    ssh-add -k  ~/.ssh/xx-2

命令行提示信息Identity added: /c/Users/Administrator/.ssh/XX-1 (/c/Users/Administrator/.ssh/XX-1)

**分别再添加到github官网设置里**
步骤略

**查看key设置**
 

    ssh-add -l
**.ssh文件夹下编辑config文件**  `vi config`
点i编辑, ESC 退出, :wq 退出保存


    # gitlab
    Host XX-1.github.com
    HostName github.com 
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/xx-1
    User xx-1

    # github
    Host XX-2.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/XX-2
    User XX-2

**测试**

     ssh -T git@XX-1.github.com   
     ssh -T git@XX-2.github.com 

 

**使用**
clone某一个仓库到本地

    
    第一个账号 git clone git@XX-1.github.com:XX-1/仓库名.git
    
    第二个账号   git clone git@XX-2.github.com:XX-2/仓库名.git
    
    提示信息Cloning into 'XX-1'...
    remote: Counting objects: 6, done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (6/6), done.

   
**给某一个仓库设置 *局部* 的用户名和邮箱**



    $ git config user.name "XX-1" 
    $ git config user.email "XX-1"
    
    $ git config user.name "XX-2" 
    $ git config user.email "XX-2"
如提示错误fatal: not in a git directory, 进入到git目录,如 /d/hexo/.deploy_git (master)

**修改上传**

    Administrator@**  MINGW64 ~/Desktop/1024c/1024 (master)

    $git add test.txt
    $git commit -m "add test.txt"
    $git push