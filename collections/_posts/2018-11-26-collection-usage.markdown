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




下面是用来展示collections用法的例子,显示出一堆staff_member的数据:


{% for staff_member in site.staff_members %}

{{ staff_member.name}} - {{staff_member.position}}
--------------------------------------------------

{{ staff_member.content | markdownify }}

{% endfor %}


OK.
