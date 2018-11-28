---
layout: post
title:  "Collection usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

Collections usages
==================

正常配置：
修改`_config.yml`,添加 `collections` 节点:

    collections:
      staff_members:
        people: true

这样，在根目录下建立一个目录`_staff_members`，然后再在这个目录下建立相应的文档。

比如: 添加一个 `./_staff_members/jane.md` 内容如下：

    ---
    name: Jane Doe
    position: Developer
    ---
    Jane has worked on Jekyll for the past *five years*.    


下面是用来展示collections用法的例子,显示出一堆staff_member的数据:


{% for staff_member in site.staff_members %}

{{ staff_member.name}} - {{staff_member.position}}
--------------------------------------------------

{{ staff_member.content | markdownify }}

{% endfor %}


添加一个单独的子目录来放collection
----------------------------------

前面这种，如果在 `_config.yml` 添加一个类型，你就需要在根目录下添加一个子目录，并添加相应的文档。
如果你觉得这样会导致collection的子目录很多的话，想把所有这些子目录放到一个单独的子目录中去，这样也是可以的。

假设，我们想把所有的collection的子目录，统一放到某个目录下，比如说，我们统一放在根目录的collections目录下。
那么,`_config.yml`配置如下：

    collections_dir: collections
    collections:
      staff_members:
        people: true

这样，我们原来要建的`_staff_members`目录，现在直接建在`./collections/_staff_members`目录下。
然后在 `_staff_members` 子目录下同样建立相应的文档。

是不是这样就Ok了呢？

不是的。
我们原来把草稿放在`./_drafts`，博客文章放在`./_posts`目录下，那么，
在指定了`collections_dir`后，这两个目录也都要转移到`collections_dir`指定的目录下。
最终的目录如下：

    .
    ├── _config.yml
    ├── _site
    ├── 404.html
    ├── about.md
    ├── collections
    │   ├── _drafts
    │   │   └── draft-note.md
    │   ├── _posts
    │   │   ├── 2018-11-26-collection-usage.markdown
    │   │   ├── 2018-11-26-jekyll-usage.markdown
    │   │   └── 2018-11-26-welcome-to-jekyll.markdown
    │   └── _staff_members
    │       ├── jane.md
    │       └── tom.md
    ├── Gemfile
    ├── Gemfile.lock
    ├── index.md

这样就可以了。


