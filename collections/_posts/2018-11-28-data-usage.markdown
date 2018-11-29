---
layout: post
title:  "data usage"
categories: [blog, jekyll]
tags: [jekyll, usage]
---

Data usage
==========


## 只有一级层级的情况 ##

建立 `_data/members.yml` 文件，里面定义一个 members 数组。然后，下面显示出来

<ul>
{% for member in site.data.members %}
<li>
    <a href="https://github.com/{{ member.github }}">{{ member.name }}</a>
</li>
{% endfor %}
</ul>


## 两个层级的情况 ##

在 `_data` 目录下建立子目录. 比如，建立 `_data/orgs`.
然后再在这个子目录下建立相应的文档。
可以具体看子目录中的文档：jekyll.yml, doeorg.yml.

<ul>
{% for org_hash in site.data.orgs %}
{% assign org = org_hash[1] %}
    <li>
    <a href="https://github.com/{{ org.username }}">
      {{ org.name }}
    </a>
    ({{ org.members | size }} members)

    {% comment %}
    || {{ org_hash }} || {{ org_hash[0] }} || {{ org_hash[1] }}
    {% endcomment %}
    </li>
{% endfor %}
</ul>

代码里面的: "assign org = org_hash[1]" .
其实，
org_hash[0] --- 返回的子目录中的数据文件的文件名;
org_hash[1] --- 返回的子目录中的内容，因为这里是yml，可以直接转化为对象访问。

