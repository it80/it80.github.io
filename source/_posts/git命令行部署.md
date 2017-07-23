---
title: 使用git命令行部署
date: 2015-01-05
---
不幸的是，上述命令虽然简单方便，但是偶尔会有莫名其妙的问题出现，因此，我们也可以追本溯源，使用git命令来完成部署的工作。

<!--more-->
    clone github repo
    
    $ cd d:/hexo/blog

    $ git clone https://github.com/jiji262/jiji262.github.io.git .deploy/jiji262.github.io

将我们之前创建的repo克隆到本地，新建一个目录叫做.deploy用于存放克隆的代码。

创建一个deploy脚本文件

    hexo generate
    cp -R public/* .deploy/jiji262.github.io
    cd .deploy/jiji262.github.io
    git add .
    git commit -m “update”
    git push origin master

简单解释一下，hexo generate生成public文件夹下的新内容，然后将其拷贝至jiji262.github.io的git目录下，然后使用git commit命令提交代码到jiji262.github.io这个repo的master branch上。

需要部署的时候，执行这段脚本就可以了（比如可以将其保存为deploy.sh）。执行过程中可能需要让你输入Github账户的用户名及密码，按照提示操作即可。

**From** https://linghucong.js.org/2016/04/15/2016-04-15-hexo-github-pages-blog/