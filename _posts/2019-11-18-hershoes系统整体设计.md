---
layout: post
title: hershoes系统整体设计
tags: 整体设计 selenium wordpress uniapp h5 android
categories: 技术原创
description: 多端展示以及内容发布系统设计
---

### 概述

学习爬虫时发现很多人都用[妹子图](www.mzitu.com)练手，使用scrapy或者selenium将妹子图的所有图片都爬出来，妹子图是一整套系统，包括：

- 图片收集
- 内容发布
- 多端展示(包括pc网站、h5网站、安卓app、iosapp)

抱着学习的心态，本人也想做一套类似的系统，做为高跟鞋控，想要展示的内容就是淘宝或者天猫的买家秀中的图片，整套系统的名字叫做hershoes，简称hs系统。整个系统的技术栈是这样：

![系统结构图](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/hs%E7%B3%BB%E7%BB%9F%E6%95%B4%E4%BD%93%E7%BB%93%E6%9E%84.png)

### 系统流程

- 浏览商品，并收集目标商品链接

  ![收集url](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/url.png)

- 开始淘宝爬虫，爬取指定商品的评论图片

  ![淘宝爬虫](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/taobao.png)

- 微博相册上，新建专辑并上传图片(暂时手动上传)

- 开始微博相册爬虫，爬取到指定专辑的图片的地址

  ![微博相册爬虫](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/weibo.png)

- 打开wordpress后台管理，新建一篇文档，将图片地址加进去并发布程序

  ![后台管理发布文章](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86.png)

- PC，H5，Android，IOS和微信客户端都可以查看图片

  ![PC](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/pc.png)

  ![H5](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/H5.jpg)

  ![Android](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/android.jpg)