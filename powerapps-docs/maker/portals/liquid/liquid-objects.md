---
title: 为门户使用 Liquid 对象 | MicrosoftDocs
description: 了解门户中的可用 liquid 对象。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 857c65097800420662aafe825f61333037b4e31c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757300"
---
# <a name="available-liquid-objects"></a>可用 Liquid 对象

Liquid 对象包含将动态内容输出到页面的属性。 例如，page 对象有一个称为 title 的属性，可用于输出当前页面的标题。

若要按名称访问对象属性，请使用点 。 要呈现模板中的对象的属性，请在 {{ 和 }} 中换行。

```
{{ page.title }}
```
也可以通过使用字符串名称和 \[\] 访问对象属性。 在动态确定所需属性，或者属性名称包含字符ߝ空格、特殊字符等会在使用 . 语法时，这非常有用。

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

下列对象可以任何位置在所有模板中使用和访问。


|   对象    |                                                                                                                                                                                          说明                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  实体   |                                                                                                 允许您按 ID 加载任何 PowerApps 实体。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [实体](#entities)                                                                                                 |
|     现在     |                                          在模板呈现时，将引用当前 UTC 时间的日期/时间对象。<br>**注释**：此值由门户 Web 应用程序缓存，不会每次刷新。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [日期筛选器](liquid-filters.md#date-filters)                                          |
|    页面     | 引用当前门户请求页面。 page 对象提供对类似于当前页面的导航痕迹、当前页面的标题或 URL、基础 PowerApps 记录的任何其他属性或相关实体等内容的访问。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [页面](#page) |
|   参数    |                                                                                                                             请求参数的便捷快捷方式。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [请求](#request)                                                                                                                              |
|   请求   |                                                                                                                        包含有关当前 HTTP 请求的信息。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [请求](#request)                                                                                                                        |
|  设置   |                                                                                                            允许您按名称加载任何[网站设置](../configure/configure-site-settings.md)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [设置](#settings)                                                                                                            |
|   站点地图   |                                                                                                                               允许访问门户站点地图。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [站点地图](#sitemap)                                                                                                                                |
| 网站标记 |                                                                                                                        允许您按名称加载任何网站标记。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [网站标记](#sitemarkers)                                                                                                                        |
|  片段   |                                                                                                         允许您按名称加载任何[内容片段](../configure/customize-content-snippets.md)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [片段](#snippets)                                                                                                         |
|    用户     |                             引用当前门户用户，允许对基础 PowerApps 联系人记录的所有属性的访问。 如果没有用户登录，此变量将为 [null](liquid-types.md#null)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [用户](#user)                              |
|  Web 链接   |                                                                                                                        允许您按名称或 ID 加载任何 Web 链接集。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [weblinks](#weblinks)                                                                                                                        |
|   网站   |                                                      引用门户网站记录，允许对门户的 PowerApps 网站 (adx\_website) 记录的所有属性的访问。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [网站](#website)                                                       |

## <a name="ads"></a>广告


提供访问和呈现广告的功能。

ads 对象允许您选择特定的广告或广告位置：

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>Ads 属性

|属性   |说明   |
|---|---|
| placements        | 返回 adplacements 对象。    |
| \[广告名称或 id\] | 可以按其名称或属性访问广告。 <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>广告位置属性

|属性   |说明   |
|---|---|
| \[广告位置名称或 id\] | 可以按其名称或 ID 属性访问任何 adplacement。<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>广告位置属性

广告位置是一个实体对象，具有所有相同属性，除了下面列出的属性之外。

|属性   |说明   |
|---|---|
| 广告            | 返回与位置关联的广告对象集合。  [迭代标记](iteration-tags.md)和[数组筛选器](liquid-filters.md#array-filters)可以与此集合一起使用。  |  
| 客户           | 返回广告位置的名称字段。                                                                |
| placement\_url | 可用于检索由模板完全呈现的广告位置的 URL。                         |
| random\_url    | 可用于从由模板完全呈现的位置检索随机广告的 URL。           |

### <a name="ad-attributes"></a>广告属性

> [!Note]
> 广告是一个实体对象，具有所有相同属性，除了下面列出的属性之外。

|属性   |说明   |
|---|---|
| ad\_url |  可用于检索由模板完全呈现的广告的 URL。   |
| 副本| 返回广告的副本字段。|
| 图像| 返回广告的图像对象（如果有）。|
| 客户| 返回广告的名称字段。|
| open\_in\_new\_window | 如果 redirect\_url 指定的 URL 应在新窗口中打开，返回 true。 |
| redirect\_url| 通过选择广告将把用户重定向到的 URL。|

### <a name="ad-image-attributes"></a>广告图像属性

|属性   |说明   |
|---|---|
| alternate\_text | 返回将显示在标记的 alt 属性中的文本。 |
| height          | 返回图像的高度（像素）                             |
| URL             | 返回图像的 URL 源。                                  |
| width           | 返回图像的宽度（像素）                              |


## <a name="blogs"></a>博客

提供访问和呈现博客和博客文章的功能。

blogs 对象允许您选择特定的博客或博客文章。

```
{% assign posts = blogs.posts | paginate: 0,4 %}

<div class=content-panel panel panel-default>

<div class=panel-heading>

{% assign sitemarker = sitemarkers[Blog Home] %}

{% assign snippet = snippets[Home Blog Activity Heading] %}

<a class=pull-right href={{sitemarker.url}}> All Blogs </a>

<h4>

<a class=feed-icon fa fa-rss-square href={{ blogs.feedpath }} />

{{ snippet.adx_value }}

</h4>

</div>

<ul class=list-group>

{% for post in posts.all %}

<li class=list-group-item >

<a class=user-avatar href={{ post.author_url }}>

<img src={{ post.user_image_url }} />

</a>

<h4 class=list-group-item-heading>

<a href={{ post.app_relative_path }}>{{ post.title }}</a>

</h4>

<div class=content-metadata>

<abbr class=timeago>{{ post.publish_date }}</abbr>

&ndash;

<a href={{ post.author_url }}> {{ post.author_name }} </a>

&ndash;

<a href={{ post.application_path }}#comments>

<span class=fa fa-comment aria-hidden=true></span> {{ post.comment_count }}

</a>

</div>

</li>

{% endfor %}

</ul>

</div>
```

### <a name="blogs-object"></a>blogs 对象

博客对象允许您访问门户中的所有特定博客，或访问门户中的所有博客文章（无论哪个博客）。

下表说明与 blogs 对象关联的属性。

|属性   |说明   |
|---|---|
| 公告               | 返回包含门户中所有博客文章的 blogposts 对象。     |
| \[博客名称或 id\] | 可以按其名称或 ID 属性访问任何博客。                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>blog 对象

blog 对象允许您处理单个博客，使您可以访问该博客的文章。

下表说明与 blog 对象关联的各个属性。

|属性   |说明   |
|---|---|
| 公告 | 返回包含博客的所有博客文章的 blogposts 对象。 |
| 客户  | 博客的名称。                                              |
| title | 博客的标题。                                             |
| URL   | 博客的 URL。                                               |

### <a name="blogposts-object"></a>blogposts 对象

blogposts 对象允许您访问博客文章对象的集合。 您可以预订博客文章，并使用 Liquid 筛选器实现分页：

{% assign blogposts = blogs.posts | order\_by “adx\_name”, “desc” | paginate: 0,4 | all %} 请注意，blogs.posts.all 也是获取所有博客文章 blogs.posts | from\_index: 0 | take 的有效方式：2 也可以

下表说明与 blogposts 对象关联的各个属性。

|属性   |说明   |
|---|---|
| 所有 | 返回集合中的所有 blogposts 对象 |

### <a name="blogpost-object"></a>blogpost 对象

引用单个博客文章。

下表说明与 blogpost 对象关联的各个属性。

|属性   |说明   |
|---|---|
| URL            | 博客的 URL。                                                                |
| content        | 返回博客的内容字段。                                             |
| content        | 返回博客的内容字段。                                             |
| author         | 返回文章的作者（即联系人实体对象）。          |
| title          | 博客的标题。                                                              |
| comment\_count | 返回指定博客评论数量计数的整数值。 |
| publish\_date  | 博客发布的日期。                                           |

## <a name="entities"></a>实体

允许您按 ID 加载任何 PowerApps 实体。 如果实体存在，实体对象将返回。 如果具有指定 ID 的实体未找到，[null](liquid-types.md#null) 将返回。  

```
{% assign account = entities.account['936DA01F-9ABD-4d9d-80C7-02AF85C822A8'] %}

{% if account %}

{{ account.name }} ({{ account.statecode.label }})

{% endif %}

{% assign entity_logical_name = 'contact' %}

{% assign contact = entities[entity_logical_name][request.params.contactid] %}

{% if contact %}

{{ contact.fullname }} ({{ contact.parentcustomerid.name }})

{% endif %}
```

### <a name="entity"></a>Entity

实体对象提供对 PowerApps 实体记录的属性的访问。


|             属性              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 编号                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    实体的 GUID ID，作为字符串。 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           logical\_name            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   实体的 PowerApps 逻辑名称。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               注释​​                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             加载与实体关联的任何注释（批注），顺序从旧到新 (createdon)。 注意作为注释对象返回。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            权限             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             加载实体的实体权限声明结果。 结果作为权限对象返回。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                URL                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    返回实体的 PowerApps 门户内容管理系统 URL 路径。 如果实体在当前网站没有有效的 URL，返回 null。 通常，这将只返回已集成到门户 CMS 的某些实体类型的值 ，除非您在您的应用程序中自定义了 URL 提供程序。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[属性或关系名称\] | 您可以按逻辑名称访问 PowerApps 实体的任何属性。 `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>大多数实体属性值直接映射到 [Liquid 类型](liquid-types.md)：“两个选项”字段映射到布尔值，文本字段到字符串，数字/货币字段到数字，日期/时间字段到日期对象。 但是，某些属性类型作为对象返回：<ul><li>查找（实体引用）字段作为实体引用对象实体。</li><li>选项集/选择列表字段作为选项集值对象返回。</li><li>您还可以通过关系架构名称来加载所有相关实体。</li>`{{ page.adx_webpage_entitylist.adx_name }}`在关系是反身（即自引用）的情况中，反身关系对象将返回。 （否则，结果是模糊的。）`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**注意**：加载大量相关实体或访问大量一个模板中的关系，可能会对模板呈现性能产生负面影响。 避免加载数组中、循环内每个项目的相关实体。 如有可能，使用 [PowerApps Common Data Service 实体标记](portals-entity-tags.md)加载实体的集合。 |

### <a name="entity-reference"></a>实体引用

查找属性值作为实体引用对象返回，具有以下属性。


|   属性   |                                                说明                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      编号       | 引用的实体的 GUID ID，作为字符串。 <br> 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| logical\_name |  引用实体的 PowerApps 逻辑名称。   |
|     客户      |                           引用实体的主名称属性。                            |

### <a name="note"></a>注释

注释是提供对注释记录的属性和关系的访问的实体对象。 除了实体对象的所有属性外，注释还具有以下额外的属性。


|  属性   |                                                                                                                                                                                                                                  说明                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | 加载注释记录的 documentbody 属性，作为 Base64 编码的字符串。 由于此属性的内容可能很大，因此不加载注释属性的其余部分，仅按需加载。 <br> **注意**：使用 documentbody 属性可能对模板呈现性能产生负面影响，应小心执行。<br>尽可能使用 url 属性提供注释附件的链接。 |
|     URL      |                                                                                                                                   返回内置门户批注附件处理程序的 URL 路径。 如果用户具有权限，且注释已附加文件，此 URL 的请求将下载注释文件附件。                                                                                                                                    |

>[!Note]
> [其他筛选器](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>选项集值

选项集/选择列表属性值作为实体引用对象返回，具有以下属性。

| 属性 | 说明                                                     |
|-----------|-----------------------------------------------------------------|
| 标签     | 选项集/选择列表属性值的本地化标签。 例如，Active|
| 值     | 选项集/选择列表属性值的整数值。 例如，0                                                           |

### <a name="entity-permissions"></a>实体权限

实体权限对象提供对实体的聚合权限声明结果的访问。

| 属性       | 说明                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| can\_append     | 如果当前用户具有将记录追加到该记录的关系的权限，返回 true。 否则，返回 false。                                                                                              |
| can\_append\_to | 如果当前用户具有将此记录追加到另一个实体的关系的权限，返回 true。 否则，返回 false。                                                                                      |
| can\_create     | 如果当前用户具有创建此实体类型的新记录的权限，返回 true。 否则，返回 false。                                                                                                      |
| can\_delete     | 如果当前用户具有删除该记录的权限，返回 true。 否则，返回 false。                                                                                                                          |
| can\_read       | 如果当前用户具有阅读该记录的权限，返回 true。 否则，返回 false。                                                                                                                            |
| can\_write      | 如果当前用户具有更新该记录的权限，返回 true。 否则，返回 false。                                                                                                                          |
| rules\_exist    | 如果该对象表示的权限结果是显式定义的权限规则的结果，返回 true。 如果是缺少显式定义权限时的默认结果，返回 false。 |

### <a name="reflexive-relationship"></a>反身关系

尝试加载实体中的反身（即自引用关系）关系作为具有以下属性的对象返回。

| 属性     | 说明                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| is\_reflexive | 返回 true。 可以用于测试关系返回的对象是否是反身关系对象。 |
| referenced    | 返回指定关系的引用实体的数组。                                           |
| referencing   | 返回指定关系的引用实体。 如果引用实体不存在，返回 null。 如果关系为多对多 (N:N)，返回引用实体的数组。                          

## <a name="entitylist"></a>entitylist

entitylist 对象在 [PowerApps Common Data Service 实体标记](portals-entity-tags.md)内使用。 它可以提供对特定实体列表所有属性的访问。  

> [!Note]                                                       
> [呈现与当前页关联的实体列表](render-entity-list-current-page.md)

### <a name="attributes"></a>属性

> [!Note]
> [entities](#entities)

|               属性               |                                                                                                                            说明                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            create\_enabled            |                                                                                如果为实体列表配置了新记录创建，将返回 true。 否则，返回 false。                                                                                |
|              create\_url              |                                                                                          为实体列表的创建链接/按钮返回已配置的 URL 路径。                                                                                          |
|            detail\_enabled            |                                                                         如果为实体列表配置了单个记录的详细信息视图，将返回 true。 否则，返回 false。                                                                          |
|         detail\_id\_parameter         |               构造记录详细信息视图 URL 时，将返回用于记录 ID 的查询字符串参数名称。 有关使用 Liquid 筛选器构造 URL 的详细信息，请参阅 [URL 筛选器](liquid-filters.md#url-filters)。 例如，id                |
|             detail\_label             |                                                                                     为实体列表的详细信息视图链接/按钮返回已配置的本地化标签。                                                                                     |
|              detail\_url              |                                                                                       为实体列表的详细信息视图链接/按钮返回已配置的 URL 路径。                                                                                        |
|           empty\_list\_text           |                                                                                当实体列表视图未返回结果时，返回要显示的已配置本地化文本。                                                                                |
|      enable\_entity\_permissions      |                                                                               如果已为此实体列表启用实体权限筛选，将返回 true。 否则，返回 false。                                                                               |
|         entity\_logical\_name         |                                                 返回此实体列表显示的记录的 PowerApps 实体逻辑名称。 例如，contact                                                 |
|   filter\_account\_attribute\_name    |                                            返回用于查找客户的属性逻辑名称，该名称将用于按当前门户用户的上级单位来筛选结果记录。 例如，accountid                                            |
|         filter\_apply\_label          |                                                            返回将高级属性筛选器应用到实体列表结果所用的链接/按钮的已配置本地化标签。                                                            |
|          filter\_definition           |                      返回实体列表的 JSON 属性筛选器定义。 有关如何使用 metafilters Liquid 筛选器处理此定义的详细信息，请参阅[实体列表筛选器](liquid-filters.md#entity-list-filters)。                       |
|            filter\_enabled            |                                                                               如果为实体列表启用了高级属性筛选，将返回 true。 否则，返回 false。                                                                               |
| filter\_portal\_user\_attribute\_name |                                                 返回用于查找联系人的属性逻辑名称，该名称将用于按当前门户用户的联系人来筛选结果记录。 例如，contactid                                                  |
|   filter\_website\_attribute\_name    |                                              返回用于查找 adx\_website 的属性逻辑名称，该名称将用于按当前门户网站来筛选结果记录。 例如，adx\_websiteid                                              |
|            language\_code             |                                               返回用于选择此实体列表的所有本地化标签的 PowerApps 整数语言代码。                                                |
|              page\_size               |                                                                                                   返回实体列表的已配置结果页面大小。                                                                                                    |
|          primary\_key\_name           |                                                                                  返回此实体列表显示的记录的主键属性逻辑名称。                                                                                  |
|            search\_enabled            |                                                                                         如果已为此实体列表启用搜索，将返回 true。 否则，返回 false。                                                                                          |
|          search\_placeholder          |                                                                                        返回实体列表搜索字段占位符的已配置本地化文本。                                                                                        |
|            search\_tooltip            |                                                                                             返回实体列表搜索工具提示的已配置本地化文本。                                                                                             |
|                 视图                 |                                                                                           以实体列表视图对象的形式返回实体列表的可用视图。                                                                                           |
|      \[属性逻辑名称\]       | 您可以按逻辑名称访问实体列表 (adx\_entitylist) PowerApps 记录的任何属性，操作方式与[实体](liquid-objects.md#entity)对象相同。 例如，{{ entitylist.adx\_name }} |

### <a name="entity-list-view-attributes"></a>实体列表视图属性

|          属性          |                                                                                     说明                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                                                         以实体列表视图列对象的形式返回视图列。                                                         |
|    entity\_logical\_name    |               返回视图中包含的记录的 PowerApps 实体逻辑名称。 例如，contact                |
|             编号              |                                                                          返回视图的 GUID ID。                                                                           |
|       language\_code        | 返回用于选择视图的所有本地化标签（列标题等）的 PowerApps 整数语言代码。 |
|            客户             |                                          返回视图的 PowerApps 显示名称。                                          |
| primary\_key\_logical\_name |        返回视图中包含的记录的 PowerApps 实体主键逻辑名称。 例如，contactid         |
|      sort\_expression       |                                               返回视图的默认排序表达式。 例如，name ASC、createdon DESC                                               |

### <a name="entity-list-view-column-attributes"></a>实体列表视图列属性

|    属性     |                                                                                    说明                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| attribute\_type  | 以字符串形式返回列的 PowerApps 属性类型名称。 例如，Lookup、Picklist、String、Boolean、DateTime |
|  logical\_name   |                       返回列的 PowerApps 属性逻辑名称。 例如，createdon                       |
|       姓名       |                      返回列的本地化 PowerApps 显示名称。 例如，Created On                       |
| sort\_ascending  |                                      返回用于按升序将列排序的排序表达式字符串。 例如，createdon ASC                                       |
| sort\_descending |                                     返回用于按降序将列排序的排序表达式字符串。 例如，createdon DESC                                      |
|  sort\_disabled  |                                                   如果禁用列的排序，将返回 true。 否则，返回 false。                                                    |
|  sort\_enabled   |                                                    如果启用列的排序，将返回 true。 否则，返回 false。                                                    |
|      width       |                                                              以像素形式返回列的已配置宽度。                                                              |

## <a name="entityview"></a>entityview

entityview 对象在 entityview 标记中使用，为视图以及视图结果记录提供对元数据的访问。

### <a name="attributes"></a>属性

|          属性          |                                                                               说明                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                         以 [entity 视图列对象](liquid-objects.md#entity-list-view-column-attributes)的形式返回视图列。                          |
| entity\_permission\_denied  | 如果对视图结果的访问由于当前用户的权限不足被拒绝，返回 true。 如果授予对视图结果的阅读访问权限，返回 false。 |
|    entity\_logical\_name    |                   视图结果记录的 PowerApps 实体逻辑名称。 例如，contact                   |
|         first\_page         |                 视图结果第一页的页码。 这将为 1，除非不返回结果，这种情况下它将是 null。                  |
|             编号              |                            定义此 entityview 的 PowerApps 视图的 GUID ID。                             |
|       language\_code        |             用于加载当前视图的本地化标签的 PowerApps 整数语言代码。              |
|         last\_page          |                                 视图结果最后一页的页码。 如果未返回结果，则将为 null。                                  |
|            名称             |              用于定义此 entityview 的 PowerApps 视图名称，如“有效联系人”。               |
|         next\_page          |                                视图结果下一页的页码。 如果结果没有下一页面，这将为 null。                                 |
|            页             |                                                           视图结果当前页面的页码。                                                           |
|            页面            |                                          返回包含当前视图的所有结果页面的页码数组。                                          |
|         page\_size          |                                                      当前视图每个页面返回的结果的数量。                                                       |
|       previous\_page        |                              视图结果下一页的页码。 如果结果没有上一页面，这将为 null。                               |
| primary\_key\_logical\_name |  此视图的结果实体的主键属性的 PowerApps 逻辑名称。 例如，contactid。   |
|           记录           |                                                   视图的结果记录的当前页面，作为实体对象。                                                    |
|      sort\_expression       |                                             视图的默认排序表达式。 例如，nameASC、createdon DESC。                                              |
|        total\_pages         |                                                              视图的结果页面的总数。                                                              |
|       total\_records        |                                                       视图的结果总数（所有页面）。                                                       |

## <a name="events"></a>事件

提供访问和呈现事件的功能。 events 对象允许您选择特定的事件或所有事件。

### <a name="events-object"></a>events 对象

events 对象允许您访问门户中的所有特定事件，或访问门户中的所有事件（无论哪个事件）。

events 对象拥有以下属性：

|属性   |说明   |
|---|---|
|occurences |返回包含门户中所有事件发生的 eventoccurancess 对象。 |
|[事件名称或 id] |可以按其名称或 ID 属性访问任何事件。<br>{% assign event = events[&quot;Event Name&quot;] %}<br>{% assign event = events[&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;] %} |

### <a name="event-object"></a>event 对象

event 对象允许您处理单个事件，使您可以访问该事件的计划和发生。

event 对象拥有以下属性：

|属性   |说明   |
|---|---|
| 发生次数 | 返回包含事件的所有发生的 eventoccurrences 对象。 |
| 名称       | 事件的名称。                                                     |
| URL        | 事件的 URL。                                                      |

### <a name="eventoccurences-object"></a>eventoccurences 对象

eventoccurrences 对象允许您访问事件发生对象的集合。 您可以对事件发生排序并指定用于检索的发生的日期范围，还可以使用 Liquid 筛选器实现分页

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

请注意

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

也有可能。

以下属性与 eventoccurrences 对象关联

|属性   |说明   |
|---|---|
| 所有 | 返回集合中的所有 eventoccurance 对象。 |

### <a name="eventoccurence-object"></a>eventoccurence 对象

表示单个事件发生。 以下给出关联的属性：

|属性   |说明   |
|---|---|
| URL                 | 发生的 URL。    |
| is\_all\_day\_event | 这是全天事件吗？     |
| start\_time         | 事件的开始时间。 |
| end\_time           | 事件的结束时间。   |


## <a name="forloop"></a>forloop

包含在 [for](iteration-tags.md#for) 循环块中有用的属性。  

> [!Note]
> forloop 只能在 [for](iteration-tags.md#for) 标记中使用。

**代码**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**输出**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| 第一   | 如果是循环的第一个迭代，返回 true。 如果不是第一个迭代，返回 false。       |
| 索引   | 当前项目在集合中的位置，其中第一个项目具有 1 位置。                   |
| index0  | 当前项目在集合中的位置，其中第一个项目具有 0 位置。                   |
| 最后一页    | 如果是循环的最后一个迭代，返回 true。 如果不是最后一个迭代，返回 false。         |
| length  | 返回循环ߝ的迭代数量，即迭代的集合中项目的数量。 |
| rindex  | 循环中其余项目的数量（长度 - 索引)，其中 1 是最后项目的索引。              |
| rindex0 | 循环中其余项目的数量（长度 - 索引）)，其中 0 是最后项目的索引。              |


## <a name="forums"></a>论坛

提供访问和呈现论坛和论坛执行绪的功能。 请注意，使用 liquid 呈现论坛数据的功能已扩展到公告，但若要创建新的公告或执行绪，您必须使用已内置前述功能的 ASP.NET Web 窗体页面模板（例如，默认论坛执行绪和论坛公告页面模板）。

论坛对象允许您选择论坛或论坛执行绪：

```
<div class=content-panel panel panel-default>

<div class=panel-heading>

<h4>

<span class=fa fa-comments aria-hidden=true></span>

{{ snippets[Home Forum Activity Heading] | default: Forum Activity | h }}

</h4>

</div>

{% for forum in website.forums %}

<ul class=list-group>

<li class=list-group-item>

<div class=row>

<div class=col-sm-6>

<h4 class=list-group-item-heading><a href="{{ forum.url | h }}"> {{ forum.name | h }}</a></h4>

<div class=list-group-item-text content-metadata>{{ forum.adx_description | h }}</div>

</div>

<div class=col-sm-3 content-metadata>{{ forum.thread_count }} threads</div>

<div class=col-sm-3 content-metadata>{{ forum.post_count }} posts</div>

</div>

</li>

</ul>

{% endfor %}

</div>
```

### <a name="forums-object"></a>论坛对象

论坛对象允许您访问门户中的所有特定论坛，或访问门户中的所有论坛执行绪（无论哪个论坛）。

forum 对象允许您处理单个论坛，使您可以访问该论坛的执行绪。

forumthreads 对象允许您访问 forumthread 对象的集合。 使用 liquid 筛选器，您可对论坛执行绪进行排序并实现分页。

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

单个论坛执行绪

forumposts 对象允许您访问 forumpost 对象的集合。

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| threads              | 返回包含门户中所有 forumthread 对象的 forumthreads 对象。             |
| 所有                  | 返回门户中的所有 forum 对象。 注意，website.forums 也是对等项。    |
| thread\_count        | 返回整个网站中执行绪数量计数的整数值。 |
| post\_count          | 返回门户中的文章总数的整数值。                       |
| \[论坛名称或 id\] | 可以按其名称或 ID 属性访问任何论坛。 <br>`{% assign forum = forums[Forum Name] %}<br>{% assign forum = forums[da8b8a92-2ee6-476f-8a21-782b047ff460] %} 

### <a name="forum-object"></a>forum 对象

### <a name="attributes"></a>属性

> [!Note]
> [实体](#entities)

|属性   |说明   |
|---|---|
| threads       | 返回包含论坛的所有论坛执行绪的 forumthreads 对象。               |
| 客户          | 论坛的名称。                                                                  |
| thread\_count | 返回论坛中执行绪数量计数的整数值。      |
| post\_count   | 返回整个论坛中公告数量计数总和的整数值。 |

### <a name="forumthreads-object"></a>forumthreads 对象

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| 所有 | 返回集合中的所有 forumthread 对象。 |

### <a name="forumthread-object"></a>forumthread 对象

### <a name="attributes"></a>属性

> [!Note]
> [entities](#entities)

|属性   |说明   |
|---|---|
| 公告        | 返回包含执行绪的所有论坛公告的 forumposts 对象。            |
| author       | 返回执行绪的作者（即联系人实体对象）。      |
| latest\_post | 返回执行绪中的最新公告。                                            |
| first\_post  | 返回执行绪中的第一个公告。                                             |
| post\_count  | 返回执行绪中公告数量计数的整数值。 |
| is\_answered | 是否应答执行绪？                                                    |
| is\_sticky   | 执行绪是否为粘滞执行绪？                                                    |

### <a name="forumposts-object"></a>forumposts 对象

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| 所有 | 返回集合中的所有 forumthread 对象。 |

单个论坛公告

### <a name="attributes"></a>属性

> [!Note] 
> [entities](#entities)

|属性   |说明   |
|---|---|
| author     | 返回文章的作者（即联系人实体对象）。 |
| content    | 公告的内容。                                                   |
| is\_answer | 此文章是否为执行绪的答案？                                      |


## <a name="knowledge"></a>知识

提供对 PowerApps knowledgearticle 和用于在门户中呈现文章和类别的类别实体记录的访问权限。

### <a name="attributes"></a>属性

|属性|说明|
|---|---|
|文章|返回包含在门户中可用的 knowledgearticle 实体记录的文章对象的文章对象。|
|类别|返回包含在门户中可用的类别实体记录的类别对象的类别对象。|
|||

### <a name="articles-object"></a>文章对象

文章对象允许您访问文章对象的集合。 通过使用 Liquid 筛选器，您可对文章进行排序并实现分页。

```
{% assign count = count | default: 3 %}
{% assign languagecode = website.selected_language.code %}
{% assign popular_articles = knowledge.articles | popular: count,languagecode  %}
{% if popular_articles %}
    <div class=list-group>
    {% for article in popular_articles %}
      <div class=list-group-item clearfix>
        <a class=title href={{ article.url | escape }}>{{ article.title | escape }}</a>
        <p class=description>{{ article.description | escape }}</p>
      </div>
    {% endfor %}
    </div>
{% endif %}
```

### <a name="attributes"></a>属性

|属性|说明|
|---|---|
|常用 |返回包含大多数视图的文章对象的集合。 `{% assign popular_articles = knowledge.articles.popular %}` |
|最近 |返回包含最新修订日期的文章对象的集合。 `{% assign recent_articles = knowledge.articles.recent %}` |
|主要 |返回包含最高评分的文章对象的集合。 `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>筛选器

以下筛选器可以接受页面大小和语言的可选参数。 第一个参数是要检索的数量或记录。 默认页面大小为 5。 第二个参数是要检索特定语言的文章的语言代码。 筛选器可与其他 [Liquid 筛选器](liquid-filters.md) 结合使用。

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|属性|说明|
|---|---|
|常用 |返回包含大多数视图的文章对象的集合。 `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|最近 |返回包含最新修订日期的文章对象的集合。 `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|主要 |返回包含最高评分的文章对象的集合。 `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>类别对象

类别对象允许您访问类别对象的集合。 您可以通过使用 Liquid 筛选器对类别排序并实现分页。

```
{% assign category_url = sitemarkers['Category'].url %}
  {% assign count = count | default: 0 %}  
  {% assign categories = knowledge.categories | top_level: count %}
  {% if categories %}
    <div class=list-group unstyled>
    {% for category in categories %}
      <a href={{ category_url | add_query: 'id', category.categorynumber }} class=list-group-item>
        {{ category.title }}
      </a>
    {% endfor %}
    </div>
  {% endif %}
```

### <a name="attributes"></a>属性

|属性|说明|
|---|---|
|最近 |返回包含最新修订日期的类别对象的集合。 |
|top_level |返回没有父类别的类别对象的集合。 |
|||

### <a name="filters"></a>筛选器

以下筛选器可以接受指示页面大小的可选参数。 默认页面大小为 5。 筛选器可与其他 [Liquid 筛选器](liquid-filters.md) 结合使用。

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|属性|说明|
|---|---|
|最近 |返回包含最新修订日期的类别对象的集合。 您可以提供参数 `{% assign recent_categories = knowledge.categories \| recent: 10 %}` |
|top_level |返回没有父类别的类别对象的集合。 `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>文章对象

文章对象允许您使用一个 knowledgearticle 在门户中显示该文章的详细信息。

### <a name="attributes"></a>属性

文章是一个[实体](#entity) 对象，除了下面列出的属性之外，还具有所有相同的属性。

|属性|说明|
|---|---|
|article_public_number| 文章的文章公共编号。|
|comment_count| 指定文章的评论数量计数的整数值。|
|content|批准文章的内容|
|current_user_can_comment|返回一个指示当前用户是否可以对文章添加评论的布尔值。|
|is_rating_enabled|返回一个指示是否对文章启用评级的布尔值。|
|keywords|文章的关键字。|
|名称|文章标题的备选别名。|
|评级|文章的十进制评分值。|
|title|文章的标题。|
|view_count|文章浏览次数的整数值。|
|||

### <a name="category-object"></a>类别对象

类别对象允许您使用一个类别在门户中显示其详细信息。

### <a name="attributes"></a>属性

类别是一个[实体](#entity) 对象，除了下面列出的属性之外，还具有所有相同的属性。

|属性|说明|
|---|---|
|categorynumber|类别的类别编号。|
|名称|类别标题的备选别名。|
|title|类别的标题。|
|||

## <a name="page"></a>页面

引用当前门户请求页面。 此对象合并[站点地图](#sitemap)和当前请求[实体](#entities)（通常是网页）的属性。  

page 对象提供对类似于当前页面的导航痕迹、当前页面的标题或 URL、基础 PowerApps 记录的任何其他属性或相关实体等内容的访问。

```
<ul class=breadcrumb>

{% for crumb in page.breadcrumbs %}

<li><a href={{ crumb.url | escape }}>{{ crumb.title | escape }}</a></li>

{% endfor %}

<li class=active>{{ page.title | escape }}</li>

</ul>

<div class=page-header>

<h1>{{ page.title | escape }}</h1>

</div>

<div class=page-copy>

{{ page.adx_copy }}

</div>

<div class=list-group>

{% for child in page.children %}

<a class=list-group-item href={{ child.url | escape }}>

{{ child.title | escape }}

</a>

{% endfor %}

</div>

<!-- Page {{ page.id }} was last modified on {{ page.modifiedon }}. -->
```

### <a name="page-attributes"></a>页面属性

> [!Note]  
> [entities](#entities)

|             属性              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            breadcrumbs             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 返回页面的导航痕迹站点地图节点对象，以站点地图根节点开头，以父项结尾。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              children              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 返回页面的子站点地图节点对象。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               上级               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           返回页面的父站点地图节点。 如果该页是主页，则父项将为 null。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               title                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                页面的标题。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                URL                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 页面的 URL。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[属性或关系名称\] | 您可以按逻辑名称访问页面的底层 PowerApps 记录的任何属性。<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>大多数实体属性值直接映射到 [Liquid 类型](liquid-types.md)：“两个选项”字段映射到布尔值，文本字段到字符串，数字/货币字段到数字，日期/时间字段到日期对象。 但是，某些属性类型作为对象返回：<ul><li>查找（实体引用）字段作为[实体引用对象](#entity-reference)返回。</li><li>选项集/选择列表字段作为[选项集值对象](#option-set-value)返回。</li> 您还可以通过关系架构名称来加载所有相关实体。 <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>在关系是反身（即自引用）的情况中，将返回[实体](#entities)对象。 （否则，结果是模糊的。）`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**注意**：加载大量相关实体或访问大量一个模板中的关系，可能会对模板呈现性能产生负面影响。 避免加载数组中、循环内每个项目的相关实体。 如有可能，尽量使用 [PowerApps Common Data Service 实体标记](portals-entity-tags.md)加载实体的集合。 |

## <a name="polls"></a>轮询

提供访问和呈现轮询的功能。

polls 对象允许您选择特定的轮询或轮询位置：

```
<div>

{% assign poll = polls[Poll Name] %}

<h4>{{ poll.question }}</h4>

{% for option in poll.options %}

<div>

<input type=radio name={{ poll.name }} id={{ option.id }} />

<label for={{ option.id }}>{{ option.answer }}</label>

</div>

{% endfor %}

<button type=button>{{ poll.submit_button_label }}</button>

</div>
```

### <a name="polls-attributes"></a>Polls 属性

|属性   |说明   |
|---|---|
| placements          | 返回 pollplacements 对象。                                      |
| \[轮询名称或 id\] | 可以按其名称或 ID 属性访问任何轮询。 `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>轮询位置属性

|属性   |说明   |
|---|---|
| \[轮询位置名称或 id\] | 可以按其名称或 ID 属性访问任何轮询位置。`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>轮询位置属性

> [!Note] 
> [实体](#entities)                                       

|属性   |说明   |
|---|---|
| 客户           | 返回轮询位置的名称字段。                            
| placement\_url | 可用于检索由模板完全呈现的轮询位置的 URL。                       |
| 轮询          | 返回与位置关联的轮询对象集合。 [迭代标记](iteration-tags.md)和[数组筛选器](liquid-filters.md#array-filters)可以与此集合一起使用。  |  
| random\_url    | 可用于从由模板完全呈现的位置检索随机轮询的 URL。         |
| submit\_url    | 向其提交已完成轮询的 URL。                                                             |

### <a name="poll-attributes"></a>轮询属性

> [!Note] 
> [实体](#entities)                                          

|属性   |说明   |
|---|---|
| has\_user\_voted       | 如果当前用户（登录或匿名）已在此轮询中投票，则返回“true”。         |
| 姓名                   | 返回轮询的名称字段。                                                              |
| 选项                | 返回与轮询关联的轮询选项对象集合。 [迭代标记](iteration-tags.md)和[实体](#entities)可以与此集合一起使用。  |  
| poll\_url              | 可用于检索由模板完全呈现的轮询的 URL。                       |
|  问题               | 返回轮询的问题字段。                                                          |
| submit\_button\_label  | 返回可用于替代轮询提交按钮标签的字符串。               |
| submit\_url            | 向其提交已完成轮询的 URL。                                                   |
| user\_selected\_option | 返回用户选择的 polloption 对象（如果已投票）。                  |
| votes                  | 返回该轮询已制成表格的投票数。                                |

### <a name="poll-option-attributes"></a>轮询选项属性

>[!Note]
> [实体](#entities)                                         

|属性   |说明   |
|---|---|
| answer     | 返回轮询的答案字段。 |
| percentage | 以 0 到 100 的十进制数返回选项轮询中的投票百分比。 |
| votes      | 返回该选项已制成表格的投票数。                              |


## <a name="request"></a>请求

包含有关当前 HTTP 请求的信息。

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> 您可以通过使用 URL 筛选器在 Liquid 中动态构建 URL。 

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| 参数           | 当前请求的指定参数值。 params 是 URL 查询字符串参数、窗体公告参数和 Cookie 的组合。  |
| 路径             | 当前请求 URL 的路径。 <br> /profile/|
| path\_and\_query | 当前请求 URL 的路径和查询。<br> /profile/?foo=1&bar=something|
| 查询            | 当前请求 URL 的查询部分。 <br> ?foo=1&bar=something |
| URL              | 当前请求的完整 URL。<br>  https://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>searchindex

searchindex 对象在 [PowerApps Common Data Service 实体标记](portals-entity-tags.md)内使用，并且提供对查询结果的访问。  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| approximate\_total\_hits | 返回与索引查询匹配的大概点击总数。 请注意，由于搜索索引工作的方式与安全筛选和其他设计因素有关，此数字仅是一个概数，某些情况下，可能无法完全匹配当前用户可用结果的总数。  |
| 页                     | 返回当前查询的页码。                                                                                                                                                                                                           |
| page\_size               | 返回当前查询的最大页面尺寸。 请注意，如果希望为当前页返回实际的结果数量（因为这可能小于指定的最大页面大小），请使用 results.size。                                                                                           |
| 结果                  | 在搜索索引结果对象时，返回查询结果页面。                                                                                                                                                                                          |

### <a name="search-index-results"></a>搜索索引结果

|   属性   |                                                                                                                                                说明                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    实体     |                                                                                                                            结果的基础[实体](#entities)。                                                                                                                            |
|   fragment    | 结果的相关短文本片段，与使用 &lt;em&gt; HTML 标记突出显示的指定查询匹配的术语。 请注意，某些查询类型不支持突出显示的片段，如模糊查询 (~) 和通配符查询 (\*)。 这些情况下该属性将为空。 |
|      编号       |                                                             结果的基本记录的 PowerApps 实体 ID，作为字符串。 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| logical\_name |                                                                           结果的基本记录的 PowerApps 实体逻辑名称。 例如，adx\_webpage                                                                           |
|    编号     |                                                            结果的数量，所有结果页，从 1 开始。 例如，第二个结果页的第一个结果，页面大小为 10，此值将为 11。                                                             |
|     score     |                                                                                                 结果的 Lucene 评分，作为浮点值。 结果将按该值排列的顺序返回。                                                                                                 |
|     title     |                                                                                                                                          结果的标题。                                                                                                                                          |
|      URL      |                                                            结果的 URL。 这通常ߝ但 &mdash;不一定&mdash; 是ߝ将当前应用程序的绝对路径，而不是完整 URL。 例如：/articles/article1/                                                             |

## <a name="settings"></a>设置

允许您按名称加载任何[网站设置](../configure/configure-site-settings.md)。 如果未找到具有指定名称的设置，将返回 [null](liquid-types.md#null)。  

> [!Note]
> 设置将返回为[字符串](liquid-types.md#string)，但是，您可以使用[类型筛选器](liquid-filters.md#type-filters)将其转换为其他类型。

```
{{ settings[My Setting] }}

{% assign search_enabled = settings[Search/Enabled] | boolean %}

{% if search_enabled %}

Search is enabled.

{% endif %}

{% assign pagesize = settings['page size'] | integer | default: 10 %}

{% if pagesize > 10 %}

Page size is greater than 10.

{% endif %}
```

> [!Note]
> [呈现网站标题和主要导航栏](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>站点地图

允许访问门户站点地图。

```
<h1>{{ sitemap.root.title }}</h1>

<ul class=breadcrumb>

{% for crumb in sitemap.current.breadcrumbs %}

<li><a href={{ crumb.title }}>{{ crumb.title }}</a></li>

{% endfor %}

<li class=active>{{ sitemap.current.title }}</li>

</ul>

{% for child in sitemap.current.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

It's also possible to load a site map node by URL path:

{% assign node = sitemap[/content/page1/] %}

{% if node %}

{% for child in node.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

{% endif %}
```

### <a name="site-map-attributes"></a>站点地图属性

|属性   |说明   |
|---|---|
| 当前 | 返回当前页面的站点地图节点对象。                    |
| 根    | 返回该网站的根（主页）页面的站点地图节点对象。 |

### <a name="site-map-node-attributes"></a>站点地图节点属性

|属性   |说明   |
|-------|-------|
| 导航痕迹           | 返回节点的导航痕迹站点地图节点对象，以站点地图根节点开头，以父项结尾。 |
| 子级              | 返回节点的子站点地图节点对象。                                                                  |
| 说明           | 节点的说明/摘要内容。 （此字段可能包含 HTML）。                                          |
| 实体                | 返回节点的基础[实体](#entities)。 如果节点没有基础实体，此值将为 null。                                                         |
| is\_sitemap\_ancestor | 如果站点地图节点是当前节点的上级节点，返回 true，否则返回 false。                                                                                                         |
| is\_sitemap\_current  | 如果站点地图节点是当前节点，返回 true，否则返回 false。                                                                                                         |
| 父级                | 返回节点的父站点地图节点。 如果节点是根节点，父项将是 null。                                                                     |
| 头衔                 | 节点的标题。                                                                                                |
| URL                   | 节点的 URL。                                                                                                  |


## <a name="sitemarkers"></a>网站标记

允许您按名称加载任何网站标记。 如果网站标记存在，将返回网站标记对象。 如果未找到具有指定名称的网站标记，将返回 [null](liquid-types.md#null)。  

```
{{ sitemarkers[Login].url }}

{% assign my_sitemarker = sitemarkers[My Site Marker] %}

{% if my_sitemarker %}

<a href={{ my_sitemarker.url }}>{{ my_sitemarker.adx_name }}</a>

{% else %}

Site marker My Site Marker does not exist.

{% endif %}
```

> [!Note]
> [呈现网站标题和主要导航栏](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>网站标记属性

|         属性          |                                                                                    说明                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            URL             |                                                                         网站标记目标的 URL。                                                                         |
| \[属性逻辑名称\] | 您可以按逻辑名称访问网站标记目标 PowerApps 记录的任何属性。 例如，{{ sitemarker.adx\_name }} |

## <a name="snippets"></a>片段

允许您按名称加载任何内容片段。 如果未找到具有指定名称的片段，将返回 [null](liquid-types.md#null)。  

```
{{ snippets[Header] }}

{% assign footer = snippets[Footer] %}

{% if footer %}

{{ footer }}

{% else %}

No footer snippet was found.

{% endif %}
```


## <a name="tablerowloop"></a>tablerowloop

包含在[迭代标记](iteration-tags.md)循环块中有用的属性。  

> [!Note] 
> forloop 只能在[迭代标记](iteration-tags.md)标记中使用。

### <a name="attributes"></a>属性

|属性   |说明   |
|---|---|
| Col        | 返回当前行的索引，从 1 开始。                                                       |
| col0       | 返回当前行的索引，从 0 开始。                                                       |
| col\_first | 如果当前列是某行中第一列，则返回 true，否则返回 false。               |
| col\_last  | 如果当前列是某行中最后一列，则返回 true，否则返回 false。                |
| 第一页      | 如果是循环的第一个迭代，返回 true。 如果不是第一个迭代，返回 false。       |
| 索引      | 当前项目在集合中的位置，其中第一个项目具有 1 位置。                   |
| index0     | 当前项目在集合中的位置，其中第一个项目具有 0 位置。                   |
| 最后一页       | 如果是循环的最后一个迭代，返回 true。 如果不是最后一个迭代，返回 false。         |
| 长度     | 返回循环ߝ的迭代数量，即迭代的集合中项目的数量。 |
| Rindex     | 循环中其余项目的数量（长度 - 索引)，其中 1 是最后项目的索引。              |
| rindex0    | 循环中其余项目的数量（长度 - 索引）)，其中 0 是最后项目的索引。              |



## <a name="user"></a>用户

引用当前门户用户，允许对基础 PowerApps 联系人记录的所有属性的访问。 如果没有用户登录，此变量将为 [null](liquid-types.md#null)。  

用户是[实体](#entity)对象。  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>属性

除了具有[实体](#entity)对象的所有属性之外，用户还具有以下属性。


|    属性     |                                                                                                                                                                                     说明                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      角色       |                                                      返回用户所属的角色，作为[数组](liquid-types.md#array)。<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**注意**：您可以使用 `has_role` 筛选器来测试各个角色成员资格。                                                       |
| basic_badges_url | 返回用于检索用户徽章的服务 URL。<br>若要呈现用户的徽章，必须包括具有“data-badge”和“data-uri”属性的标记。 要呈现当前用户的徽章：<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>要按 ID（可变 userid）呈现用户的徽章：<br>\`<div data-badge data-uri='{{user.basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>Web 链接

允许您按名称或 ID 加载任何 weblinks。  

如果 Web 链接集存在，[Web 链接集对象](#web-link-set-attributes)将返回。 如果具有指定名称或 ID 的 Web 链接集未找到，[null](liquid-types.md#null) 将返回。


```
<!-- Load web link set by ID -->

{{ weblinks[page.adx_navigation.id].name }}

<!-- Load web link set by name -->

{% assign nav = weblinks[Primary Navigation] %}

{% if nav %}

<h1>{{ nav.title | escape }}</h1>

<ul>

{% for link in nav.weblinks %}

<li>

<a href={{ link.url | escape }} title={{ link.tooltip | escape }}>

{% if link.image %}

<img src={{ link.image.url | escape }} alt={{ link.image.alternate_text | escape }} />

{% endif %}

{{ link.name | escape }}

</a>

</li>

{% endfor %}

</ul>

{% endif %}
```

> [!Note]
> [呈现网站标题和主要导航栏](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Web 链接集属性

> [!Note]
> Web 链接集是一个[实体](#entity)对象，除了下面列出的属性之外，还具有所有相同的属性。                                         

|         属性          |                                                                                 说明                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            副本            |                                                                      Web 链接集的 HTML 副本。                                                                      |
|            客户            |                                                                        Web 链接集的名称。                                                                         |
|           头衔            |                                                                        Web 链接集的标题。                                                                        |
|          Weblinks          |                                                       与 Web 链接集关联的 Web 链接对象的数组。                                                        |
| \[属性逻辑名称\] | 您可以按逻辑名称访问 Web 链接集 PowerApps 记录的任何属性。 例如，{{ weblinkset.createdon }} |

### <a name="web-link-attributes"></a>Web 链接属性

> [!Note]
> Web 链接是一个[实体](#entity)对象，除了下面列出的属性之外，还具有所有相同的属性。

|          属性          |                                                                              说明                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         说明         |                                                                 Web 链接的 HTML 说明。                                                                 |
|    display\_image\_only     |                              指示 Web 链接是否应仅作为图像显示而不包含链接文本的布尔属性。                               |
| display\_page\_child\_links |            指示 Web 链接是否应作为子链接显示指向链接页面的[*站点地图*](#sitemap)子页面的链接的布尔属性。             |
|            图像            |                                     此链接的 Web 链接图像对象。 如果图像不存在，则此属性将为空。                                      |
|        is\_external         |                 指示 Web 链接的目标 URL 是否是到外部网站（而不是到内部门户页面）的布尔属性。                  |
|    is\_sitemap\_ancestor    |                                如果 Web 链接的 URL 引用当前站点地图节点的上级节点，返回 true，否则返回 false。                                 |
|    is\_sitemap\_current     |                                        如果 Web 链接的 URL 引用当前站点地图节点，返回 true，否则返回 false。                                        |
|            姓名             |                                                                    Web 链接的名称/标题。                                                                    |
|          Nofollow           |                                         指示 Web 链接是否应标记为 rel=nofollow 的布尔属性。                                         |
|    open\_in\_new\_window    |                             指示选择后 Web 链接是否应该在新浏览器窗口/选项卡中打开的布尔属性。                             |
|           工具提示           |                                                                    Web 链接的工具提示文本。                                                                     |
|             URL             |                                                                       Web 链接的 URL。                                                                        |
|          Weblinks           |                                                   与 Web 链接集关联的子 Web 链接对象的数组。                                                   |
| \[属性逻辑名称\]  | 您可以按逻辑名称访问 Web 链接 PowerApps 记录的任何属性。 例如，{{ weblink.createdon }} |

### <a name="web-link-image-attributes"></a>Web 链接图像属性

| alternate\_text | 图像的替换文本。                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| 高度          | 包含指定图像高度的整数。 如果未提供高度值，该属性将为空。 |
| URL             | 图像的 URL。                                                                                               |
| 宽度           | 包含指定图像宽度的整数。 如果未提供宽度值，该属性将为空。   |


## <a name="website"></a>网站

引用门户网站，允许对门户的 PowerApps 网站 (adx\_website) 记录的所有属性的访问。  

> [!Note]
> 网站是一个[实体](#entity)对象，具有所有相同属性。

**代码**

```
{{ website.adx_name }} ({{ website.id }})
```

**输出**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>另请参阅

[Liquid 类型](liquid-types.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md)  
