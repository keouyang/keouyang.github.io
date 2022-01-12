---
title: 
date: ###
categories: hexo,yilia
tags: yilia
keywords: yilia
---

# 基于yilia主题优化bolg的页面和功能
- - - -
<!--more-->
## 注意#如果是注释的开头不能顶格写
## 1.配置所有文章选项
**点击全部文章会出现问题，找不到文章**
*终端先到blog目录下*
*执行 npm i hexo-generator-json-content --save *
*在_config.yml文件下增加下列内容，注意每一行对应的间隔数,和冒号之后的空格*
```
jsonContent:
    meta: false
    pages: false
    posts:
      title: true
      date: true
      path: true
      text: false
      raw: false
      content: false
      slug: false
      updated: false
      comments: false
      link: false
      permalink: false
      excerpt: false
      categories: false
      tags: true
```
- - - -
## hexo配置sitemap和keywords
**主要是对搭建的blog进行简单的seo，比如给每篇文章加上keywords,以及生成sitemap.xml文件，方便搜索引擎的搜索**
```
//终端转到blog目录下
npm install hexo-generator-sitemap --save
```
**在blog的根目录下找到_config.yml文件，增加如下代码**
```
sitemap:
    path: sitemap.xml
```
**设置hexo博客的关键字**
```
//在blog的_config.yml下修改，采用英文逗号隔开，注意kewords和关键字之间的空格
 # Site
title: 站点标题
subtitle: 站点副标题
description: 站点描述
author: 站点作者timeiidzone:
keywords: 前端博客,JavaScript,html5,css3,Jquery,NodeJs,Ubuntu（#博客关键字） 
```
**设置文章的关键字**
**需要在blog/themes/yilia/layout/_partial下找到head.ejs文件，添加如下代码**
```
<% if (page.keywords){ %>
<meta name="keywords" content="<%= page.keywords %>,<%= config.keywords %>">
<% } else if (config.keywords){ %>
<meta name="keywords" content="<%= config.keywords %>">
<%} %>
```
**上述代码的意思可以解释为：如果页面有关键字，使用页面关键字，否则使用配置文件的关键字**
**在文章开头加入keywords**
**不要在代码框内加 - - - 会出现问题！！！**
```
title: ###
date: ###
categories: ###
tags: ###
keywords: ###
```
- - - -
## hexo设置主题头像等图片
**存放位置**
- - - -
存放在/themes/yilia/source/的任意位置，可以自己新建一个文件夹，如assets，然后在assets下建立img文件夹
- - - -
**文件的配置**
- - - -
配置文件为/themes/yilia/_config.yml
```
root: /themes/yilia/source/ ##设置根目录
 # 微信二维码图片
weixin:  /assets/img/wechat.png
 # 头像图片
avatar:  /assets/img/head.jpg
 # 网页图标
favicon:  /assets/img/head.jpg
```
- - - -
## hexo设置主页标签和个性签名
```
//在全局配置文件_config.yml中进行如下的修改
title: KOY  //站点标题
subtitle: KOY  //站点副标题
description: 个人技术博客  //站点描述
keywords: 前端博客，后端博客 //博客关键字
author: OUYANG  //作者
language: zh-CN  
timezone:
'''
以上的修改只能改变改变屏幕左下角的名字和网页的名字，如果想要修改头像下面的昵称需要修改yilia目录下的_config.yml文件，加上以下内容
- - - -
```
 # Site
title: KOY  
subtitle:
description: 个人技术博客
keywords: Hexo,c++,slam
author: OUYANG  
language: zh-CN  
timezone:
```
- - - -
个性签名也在此文件aboutme处修改
- - - -
## 设置文章只显示摘要
- - - -
在_posts的md文件中正文里面添加 <!--more--> 
将显示more上面的内容作为文章的摘要，下面内容将隐藏，点击more将显示全文
- - - -
```
 #通过修改下面文字，可以改变链接的文字
excerpt_link: more //例如我将其改称展开说说
```
- - - -
