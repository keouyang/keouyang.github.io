---
title: 
date: ###
categories: hexo,yilia
tags: yilia
keywords: yilia
---

# 解决hexo插入图片无法正常显示
- - - -
<!--more-->
## 绝对路径
**图片只能放在source文件夹下可以建立一个名为image的文件夹，自己尝试放在其他地方发现不可行**
*调用图片的方法*
```
![图片的描述](/image/xxx.png)
```
- - - -
## 相对路径
**首先需要修改_config.yml文件中的配置post_asset_folder设为true后，执行命令hexo new 文章名，在source/_posts中会生成与文章名相同的文件夹和一个文章名.md文件，将对应的图片放入对应的source/_posts文件夹下。即可使用相对路径引用图片资源。**
```
![](image.jpg)
```


