---
layout: post
title:  "Collection usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

Collections usages
==================

下面是用来展示collections用法的例子,显示出一堆staff_member的数据:


{% for staff_member in site.staff_members %}

{{ staff_member.name}} - {{staff_member.position}}
--------------------------------------------------

{{ staff_member.content | markdownify }}

{% endfor %}


OK.
