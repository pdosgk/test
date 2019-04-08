---
currentMenu: content_tag
---


#内容模块  
>内容模块PC标签调用说明  
>模块名content_tag  

调用示例  
```php
<?php $page_list=content_tag('lists', ['catid' => 13, 'num' => 20, 'order' => 'id DESC']);?>
<foreach name="page_list" item="v">
    <li><span>05-17</span> <a href="{:getUrl($v['catid'], $v['id'])}" target="_blank" title="{$v[title]}" style="color:red;">{$v[title]}</a></li>
</foreach>
```

模块提供的可用操作

操作名 | 说明
-|-
lists |   内容数据列表
category |    内容栏目列表
position  |   内容推荐位列表
relation |    内容相关文章
hits |    内容数据点击排行榜

---


###内容列表(lists)
可用参数：

参数名 | 是否必须  |    默认值 | 说明
-|-|-|-
catid |   否  |   null |    调用栏目ID
where |   否  |   null |    sql语句的where部分
thumb |   否  |   0 |   是否仅必须缩略图
order |   否  |   null |    排序类型
num | 是  |   null |    数据调用数量
moreinfo |    否  |   0 |   是否调用副表数据

代码例子：
```php
<?php $page_list=content_tag('lists', ['catid' => 13, 'num' => 20, 'order' => 'id DESC']);?>
<foreach name="page_list" item="v">
    <li><span>05-17</span> <a href="{:getUrl($v['catid'], $v['id'])}" target="_blank" title="{$v[title]}" style="color:red;">{$v[title]}</a></li>
</foreach>
```

返回参数如下表：

 

字段 |  类型 |  空 |   默认 |  注释
-|-|-|-|-
title |   char(80) |    否 |   NULL |    推荐位标题
url | char |   否  |  NULL |    推荐位链接地址
inputtime |   int(10) | 否  |  NULL  |   推荐位发布时间
thumb |   char |    是 |   NULL |    推荐位缩略图
其他  | 不定 |  是  |     |  其他模型字段

---

###栏目列表（category）：
可用参数：

参数名 | 是否必须 |    默认值 | 说明
-|-|-|-
catid |   否 |   0 |   调用该栏目下的所有栏目 ，默认0，调用一级栏目
$siteid | 否 |   1 |   默认调用系统站点
order |   否  |  null |    排序方式、一般按照listorder ASC排序，即栏目的添加顺序

代码例子：
```php
<?php $category_list=content_tag(category, ['catid' => 0, 'limit' => 8]);?>
<foreach name="category_list" item="r">
    <li><a href="{:getUrl($r['catid'])}">{$r['catname']}</a>
</foreach>
```

返回参数如下表：
字段   |   类型  |   默认值     |   说明 
-|-|-|-
catid   |   smallint    |   无   |    栏目ID
siteid  |   tinyint(3)  |    0  |    站点ID
module  |   varchar(15) |    无  |    模块ID
type    |   tinyint(1)  |    1  |    栏目类型ID
modelid |   tinyint(5)  |    5  |    模型ID
parentid    |   smallint(5) |    5  |    上级父栏目
arrparentid |   varchar(255)    |    无  |    所有父栏目
child   |   tinyint(1)  |    0  |    子栏目
arrchildid  |   mediumtext  |    无  |    所有子栏目
catname |   varchar(30) |    无  |    栏目名称
image   |   varchar(100)    |    无  |    栏目图片
description |   mediumtext  |    无  |    栏目描述
parentdir   |   varchar(100)    |    无  |    父栏目目录
catdir  |   varchar(30) |    无  |    栏目目录
url |   varchar(100)    |    无  |    栏目链接
items   |   mediumint(8)    |    0  |    栏目内容数
hits    |   int(10) |    0  |    点击数
setting |   mediumtext  |    无  |    栏目设置
listorder   |   smallint(5) |    0  |    排序
ismenu  |   tinyint(1)  |    0  |    是否显示
sethtml |   tinyint(1)  |    0  |    是否生成到根目录
letter  |   varchar(30) |    无  |    栏目拼音
