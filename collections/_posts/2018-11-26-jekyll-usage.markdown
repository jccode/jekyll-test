---
layout: post
title:  "Jekyll usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

+ 如何创建自定义的页面(Page).
  - 在根目录下创建
  - 在根目录下创建一个子目录来组织自定义的页面
  
+ 创建 `Post`
  - 直接在 `_posts` 目录下创建 `YEAR-MONTH-DAY-title.MARKUP` 文件,然后编写,即可.
  - 文件头需要有 [front matter](https://jekyllrb.com/docs/front-matter/ ) 
  - 连接到其他文件,使用 `post_url`, 也可以指定资源文件等,如图片,放到 `assets` 目录下.
  - 指定分类(`categories`)和标签(`tags`).
  - 博客摘要.默认使用第一段的内容做为摘要. 也可以在 `front-matter` 中通过变量( `excerpt_separator` )指定摘要的分隔符.
  - 草稿. 创建一个 `_drafts` 目录(在根目录下). 然后创建没有带日期的md文件即可. 作为草稿,并不会发布出去. 启动时,指定`--draft`参数,可以查看草稿文件.

+ Front matter
  - 预定义的全局变量: layout, permalink, published
  - 自定义变量. 挂在 page 对象下面, 如: page.foo
  - Post下的预定义的变量: date, category/categories, tags

+ Collections [usage]({{ site.baseurl }}{% post_url 2018-11-26-collection-usage %} ) 

+ Data files
  - 数据文件放到`_data`目录下，支持`csv`,`yaml`,`yml`,`json`等数据格式
  - 然后通过`site.data`进行访问




