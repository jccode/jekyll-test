---
layout: post
title:  "Image usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

# Image usage #

下面是图片的例子:

{% assign image_files = site.static_files | where: "image", true %}
{% for img in image_files %}
<img src="{{ img.path | relative_url }}" alt="{{ img.name }}"/>
{% endfor %}

