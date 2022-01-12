---
title: 
date: ###
categories: hexo
tags: ###
keywords: hexo,blog
---

# hexo-blog框架的搭建
- - - -
<!--more-->
## 安装Nodejs
1. 安装node.js
   node -v #查看node的版本
2. 安装npm包管理器
   npm -v #查看npm的版本
3. 利用npm安装cnmp淘宝的源
   npm install -g cnpm --registry=http://registry.npm.taobao.org	#安装淘宝的cnpm 管理器
   cnpm -v	#查看cnpm版本
- - - -
## 安装hexo
1. cnpm install -g hexo-cli    #安装hexo框架
2. hexo -v #查看hexo的版本
- - - -
## 创建blog
1. pwd 查看当前路径
2. mkdir blog	#创建blog目录
   如果搭建blog过程中出现问题，可以把刚刚创建的blog文件夹删除，重新开始
3. cd blog
   hexo init #初始化一个blog 我这边没有加sudo，感觉也还行
   结束后可以在blog文件夹下查看生成的文件
4. 启动blog hexo start 简写：hexo s
5. hexo n "blog名" 新建一篇文章
   将在source/_posts/下生成
6. cd 到blog下
   hexo clean #清理一下
   hexo generate 简写hexo g 生成
7. hexo s -p 端口号 暂时修改启动端口 
   hexo s 默认启动端口为4000，可能被占用
- - - - 
## 将blog部署到github
1. 登陆github,new repository
2. 命名仓库
   必须是自己的昵称.github.io
3. create
4. 在blog目录下安装一个部署到git的插件
   cnpm install --save hexo-deployer-git #在blog目录下安装git部署插件
5. 设置_config.yaml
   ```
   # Deployment
   ## Docs: https://hexo.io/docs/one-command-deployment
   deploy:
     type: git
     repo: https://github.com/keouyang/keouyang.github.io.git #仓库地址
     branch: master
  ``` 
6. 部署到远端
   hexo d 
   现在不能用账号密码登陆，需要去github上申请令牌
   https://YourGithubName.github.io/  #访问这个地址可以查看博客
7. 更换blog主题
   cd blog
   git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia  #下载yilia主题到blog下的themes
   修改_config.yml文件
   ```
   # Extensions
   ## Plugins: https://hexo.io/plugins/
   ## Themes: https://hexo.io/themes/
   theme: yilia #使用的主题
   ```
   hexo clean 
   hexo g
   hexo s -p 端口号 #本地部署
   hexo d #部署到git

