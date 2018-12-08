---
layout: post
title:  "Jekyll usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

# 如何创建自定义页面 #

- 在根目录下创建
- 在根目录下创建一个子目录来组织自定义的页面


# 如何创建`Post` #

- 直接在 `_posts` 目录下创建 `YEAR-MONTH-DAY-title.MARKUP` 文件,然后编写,即可.
- 文件头需要有 [front matter](https://jekyllrb.com/docs/front-matter/ ) 
- 连接到其他文件,使用 `post_url`, 也可以指定资源文件等,如图片,放到 `assets` 目录下.
- 指定分类(`categories`)和标签(`tags`).
- 博客摘要.默认使用第一段的内容做为摘要. 也可以在 `front-matter` 中通过变量( `excerpt_separator` )指定摘要的分隔符.
- 草稿. 创建一个 `_drafts` 目录(在根目录下). 然后创建没有带日期的md文件即可. 作为草稿,并不会发布出去. 启动时,指定`--draft`参数,可以查看草稿文件.


# Front matter #

- 预定义的全局变量: layout, permalink, published
- 自定义变量. 挂在 page 对象下面, 如: page.foo
- Post下的预定义的变量: date, category/categories, tags


# Collections #

- [usage]({{ site.baseurl }}{% post_url 2018-11-26-collection-usage %} ) 


# Data files #

- 数据文件放到`_data`目录下，支持`csv`,`yaml`,`yml`,`json`等数据格式
- 然后通过`site.data`进行访问


# Assets #

主要指sass,coffee文件.

## SASS ##

SASS文件分两种:

- 主文件,最终要生成输出文件的,如:`_site/css/style.css`.
- 库文件,最终不需要生成输出文件,典型的,在SASS中,它是给主文件`@import`的.

对于第1种,主文件的生成,目录结构是原样输出,扩展名会从`sass`或者`scss`编译成相应的`css`.
比如,你定义一个`./css/style.scss`,那么,Jekyll会编译生成`./_site/css/style.css`.
主文件的内容,必须要定义`Front matter`,见下面的例子.
只有定义了`Front matter`,Jekyll才会把它当做一个普通文件处理,才会产生输出.
如果不定义`Front matter`,那么这个文件对于Jekyll而言,相当于是隐形的,不会当作原文件处理,而不产生输出.

对于第2种,库文件,默认是定义在`./_sass`目录中(它是由参数`sass_dir`定义的).
它就是普通的`sass`文件,不需要定义`Front matter`,从而不产生输出,只给别人`@import`.


例子:

比如你可以创建`./css/style.scss`文件, 文件内容如下:


    ---
    ---

    // your scss definitions
    .my-css-definitions { font-size: 1.2em }


那么, Jekyll会为你生成`./css/style.css`在`_site`目录下.
注意文件前面的`Front matter`(两个三横线)是必要的.
只有这个空的Front matter,Jekyll才会把这个文件当成要处理的文件,才会在`_site/css/`目录下输出文件.


## Coffeescript ##

jekyll 3.0 以上，
- 安装 `jekyll-coffeescript` gen
- `_config.yml`中添加相应的插件

        plugins:
        - jekyll-coffeescript


# 静态文件(static_files) #

比如，把图片放到 `./assets/img` 目录下.

修改 `_config.yml` , 添加 Front Matter:

    defaults:
      - scope:
          path: "assets/img"
        values:
          image: true

然后, [访问图片]({{ site.baseurl }}{% post_url 2018-11-30-image-usage %}).


# 分页(Paginate) #

## 添加插件 ##

Jekyll 3需要添加`jekyll-paginate`插件.
Jekyll 2不需要这一步,分页是标准插件.

1. 修改 `_config.yml`,在`plugins`键下,增加`- jekyll-paginate`.
2. 修改 `Gemfile`,在`group :jekyll_plugins do`下,增加`gem "jekyll-paginate"`.
3. 添加完成后,执行`bundle install`.

关于 [如何添加plugin](https://jekyllrb.com/docs/plugins/installation/ ), [Jekyll分页](https://jekyllrb.com/docs/pagination/ ) .


## 配置分页 ##

添加插件完成后,就是配置了. 修改`_config.yml`, 添加下面的配置:

    paginate: 5
    paginate_path: "/blog/page:num/"

第一个`paginate`指明分页的页数,
后面一个`paginate_path`是分页的路径,`:num`是分页的页码.

比如,按照上面的配置,我们则必须在`blog`目录下建一个`index.html`,里面是要显示分页相关的代码.
然后jekyll会根据这个文件做为模板,为我们生成分页的页面(当我们的posts数量超过5个的时候).

我们假设一共有12个,生成的逻辑是:

前5个posts会生成在`/blog/index.html`页面中,
然后,接下来的5个posts会生成在`/blog/page2/index.html`,依此类推,
最后的两个会生成在`/blog/page3/index.html`中.

# 其他 #

Jekyll只处理有`Front matter`的文件, [参考](https://jekyllrb.com/docs/variables/ ) .

