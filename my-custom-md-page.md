---
# custom page: by md file.

layout: home
---

My custome page on Jekyll on root directory
===========================================

Pages are the most basic building block for content. They’re useful for standalone content (content which is not date based or is not a group of content such as staff members or recipes).

创建最简单的方法，就是在根路径下创建一个html文件（也可以是md文件），最终由`Jekyll`生成。生成后的文件在`_site`目录下.
如果自定义的文件多的话,也可以组织到子目录中去. `Jekyll`在生成的时候,会把子目录的结构生成到对应的 `_site`的子目录中去.

访问的URL是按照目录名和文件名来的.如果你想拥有不同的访问路径,可以使用 [permalinks](https://jekyllrb.com/docs/permalinks/ ) .

