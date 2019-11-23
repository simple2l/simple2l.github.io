---
layout: post
title: 三、wordpress中图片主题iphoto的使用和修改
tags: wordpress 主题 iphoto
categories: 技术原创
description: wordpress中图片主题iphoto的使用和修改
---

### 概述

![系统结构图](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/hs%E7%B3%BB%E7%BB%9F%E6%95%B4%E4%BD%93%E7%BB%93%E6%9E%84.png)

hs系统的内容发布，使用的是wordpress，[WordPress是使用PHP语言开发的博客平台](https://baike.baidu.com/item/WordPress/450615?fr=aladdin)。经过搜索，找到了一个合适的[主题iphoto](http://www.2zzt.com/tupianzhuti/2354.html)，但是安装wordpress(版本 5.2.3 )和设置主题的时候，还有一点问题，记录下来。

### xampp

####  安装

XAMPP（Apache+MySQL+PHP+PERL）是一个功能强大的建站集成软件包。这个软件包原来的名字是 LAMPP，但是为了避免误解，最新的几个版本就改名为 XAMPP 了。 windows[下载安装包](https://www.apachefriends.org/download.html)安装即可。

#### 启动

打开xampp面板，启动apache和mysql

![面板](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/xampp%20panel.png)

### wordpress下载安装

官网下载后，解压到htdocs，如下：

![wordpress目录](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/wordpress.png)

浏览器访问http://127.0.0.1/wordpress安装:

![install](https://raw.githubusercontent.com/liuleidong/MarkdownImg/master/hs/wordpress_install.png)

在xampp面板的MySQL，点击Admin按钮打开phpmyadmin，创建一个数据库：

![创建数据库](https://github.com/liuleidong/MarkdownImg/blob/master/hs/wordpress_dbc.png?raw=true)

浏览器中点击"现在就开始"按钮并填写信息：

![数据库信息](https://github.com/liuleidong/MarkdownImg/blob/master/hs/wordpress_db.png?raw=true)

注意生产环境中，密码切勿是空的

![安装完成](https://github.com/liuleidong/MarkdownImg/blob/master/hs/insall_done.png?raw=true)

设置站点信息并开始安装

![安装](https://github.com/liuleidong/MarkdownImg/blob/master/hs/wordpress_title.png?raw=true)

![安装完成后登录](https://github.com/liuleidong/MarkdownImg/blob/master/hs/login.png?raw=true)

访问 http://127.0.0.1/wordpress/ 即可看到默认主题的站点

### wordpress主题启用

将下载的主题解压，放入wordpress对应目录：

![解压放入](https://github.com/liuleidong/MarkdownImg/blob/master/hs/theme.png?raw=true)

登录后台管理，进入外观=>主题设置界面，启用主题

![启用](https://github.com/liuleidong/MarkdownImg/blob/master/hs/theme_on.png?raw=true)

设置插件为启用 WizyLike WP-Img WP-PostViews

![插件](https://github.com/liuleidong/MarkdownImg/blob/master/hs/plugins.png?raw=true)

查看站点

![站点](https://github.com/liuleidong/MarkdownImg/blob/master/hs/error.png?raw=true)

### 发布文章

打开后台管理，添加文章，填写标题和图像区块

![添加](https://github.com/liuleidong/MarkdownImg/blob/master/hs/add_post.png?raw=true)

图片可以上传添加，也可以输入url查看

![url](https://github.com/liuleidong/MarkdownImg/blob/master/hs/add_post1.png?raw=true)

完成后，发布文章

![文章](https://github.com/liuleidong/MarkdownImg/blob/master/hs/post.png?raw=true)

### 问题：iphoto主题显示的图集只显示两个

wp-content/themes/iphoto/index.php中有如下代码

```php+HTML
<?php get_header(); ?>
	<div id="cate" data-type="index" data-name="index"></div>
	<div id="container">
		
		<?php if(have_posts()):
			$paged = (get_query_var('paged')) ? get_query_var('paged') : 1;
			$paged = $paged*4-3;
			$prePage = get_option('posts_per_page')/4;
			if(isset($_GET['order'])){
				$paged = (get_query_var('paged')) ? get_query_var('paged') : 1;
				$args = array(
					'meta_key' => $_GET['order'],
					'orderby'   => 'meta_value_num',
					'showposts'=> $prePage,
					'paged' => $paged,
					'order' => DESC
				);
			}else{
				$args = array(
					'showposts'=>$prePage,
					'paged' => $paged
				);
			}
			query_posts($args);
			while (have_posts()) : the_post(); ?>
			<?php get_template_part( 'content', get_post_format() ); ?>
		<?php endwhile; endif; ?>
	</div>
	<div id="pagenavi">
		<?php pagenavi();?>
	</div>
<?php get_footer(); ?>
```

`$prePage = get_option('posts_per_page')/4;`

posts_per_page在后台管理界面中，可以设置最多显示多少文章

![显示](https://github.com/liuleidong/MarkdownImg/blob/master/hs/page.png?raw=true)

设置大一些即可

![主页](https://github.com/liuleidong/MarkdownImg/blob/master/hs/hs.png?raw=true)

### 最终效果

PC:www.hershoes.top

手机H5:[m.hershoes.top](www.hershoes.top)

安卓客户端：http://hershoes.top/hhs.apk

