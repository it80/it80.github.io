---
title: 为 Hexo 博客添加 404 页面
date: 2015-01-01
---
404页面效果 https://it80.github.io/404

创建一个页面
在hexo项目根目录输入命令
`hexo new page 404`
这时会创建source/404/index.md文件
<!--more-->
修改设置信息
修改source/404/index.md的头部为
页面选择腾讯公益
```
layout:  false 
comments:  false
permalink:   /404.html
---
<html>
<head>
</head>
<body>
<script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8" homePageUrl="http://leyar.me" homePageName="返回主页"></script>
</body>
</html>
```
将homePageUrl="" 引号内的内容改成你的网址