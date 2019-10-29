---
title: 为门户使用液体对象 |MicrosoftDocs
description: 了解门户中可用的液体对象。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 05e3dfbeb2c3356821a0952ed14a1924e657c293
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976636"
---
# <a name="available-liquid-objects"></a>可用 Liquid 对象

液体对象包含将动态内容输出到页面的属性。 例如，page 对象具有一个名为 title 的属性，该属性可用于输出当前页的标题。

若要按名称访问对象属性，请使用点。 若要在模板中呈现对象的属性，请将其包装在 {{和}} 中。

```
{{ page.title }}
```
还可以通过使用字符串名称和 \[\]来访问对象的特性。 当所需属性是动态确定的，或者属性名称包含在使用时无效的字符、空格、特殊字符等时，这非常有用。 语法.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

可以在任何模板中的任何位置使用和访问以下对象。


|   对象    |                                                                                                                                                                                          描述                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  条目   |                                                                                                 允许你按 ID 加载任何 PowerApps 实体。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][实体](#entities)                                                                                                 |
|     现在     |                                          引用模板时当前 UTC 时间的日期/时间对象。<br>**注意**：此值由门户 web 应用缓存，每次都不会刷新。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][日期筛选器](liquid-filters.md#date-filters)                                          |
|    分页     | 引用当前门户请求页。 Page 对象提供对当前页的痕迹导航、当前页的标题或 URL 以及基础 PowerApps 记录的任何其他属性或相关实体的访问权限。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][页面](#page) |
|   params    |                                                                                                                             用于 request 的便利快捷方式。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][请求](#request)                                                                                                                              |
|   需要   |                                                                                                                        包含当前 HTTP 请求的相关信息。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][请求](#request)                                                                                                                        |
|  设置   |                                                                                                            允许按名称加载任何[站点设置](../configure/configure-site-settings.md)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][设置](#settings)                                                                                                            |
|   站点地图   |                                                                                                                               允许访问门户网站图。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][站点地图](#sitemap)                                                                                                                                |
| sitemarkers |                                                                                                                        允许按名称加载任何站点标记。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [sitemarkers](#sitemarkers)                                                                                                                        |
|  片段   |                                                                                                         允许按名称加载任何[内容片段](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/customize-content-snippets)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][代码段](#snippets)                                                                                                         |
|    用户     |                             指当前门户用户，允许访问基础 PowerApps 联系人记录的所有属性。 如果没有用户登录，则此变量将为[null](liquid-types.md#null)。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][用户](#user)                              |
|  weblinks   |                                                                                                                        允许你按名称或 ID 加载任何 Web 链接集。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [weblinks](#weblinks)                                                                                                                        |
|   网站   |                                                      指门户网站记录，允许访问门户的 PowerApps 网站（adx\_网站）记录的所有属性。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][网站](#website)                                                       |

## <a name="ads"></a>广告


提供访问和呈现广告的能力。

Ads 对象允许选择特定的广告或广告位置：

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>广告特性

|Attribute   |描述   |
|---|---|
| 布置        | 返回 adplacements 对象。    |
| \[ad 名称或 id\] | 可以通过名称或 Id 属性访问任何 ad。 <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>广告放置属性

|Attribute   |描述   |
|---|---|
| \[ad 位置名称或 id\] | 可以按名称或 Id 属性访问任何 adplacement。<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>广告放置属性

除了下面列出的属性外，ad 位置是具有所有相同属性的实体对象。

|Attribute   |描述   |
|---|---|
| 广告            | 返回与放置关联的 ad 对象的集合。  [迭代标记](iteration-tags.md)和[数组筛选器](liquid-filters.md#array-filters)可用于此集合。  |  
| 名称           | 返回广告位置的名称字段。                                                                |
| 放置\_url | 可用于检索模板完全呈现的广告位置的 URL。                         |
| 随机\_url    | 可用于从模板完全呈现的位置检索随机广告的 URL。           |

### <a name="ad-attributes"></a>Ad 属性

> [!Note]
> Ad 是一个实体对象，除了下面列出的属性外，还有所有相同属性。

|Attribute   |描述   |
|---|---|
| ad\_url |  可用于检索模板完全呈现的广告的 URL。   |
| 复本| 返回广告的复制字段。|
| 影像| 返回广告的图像对象（如果有）。|
| 名称| 返回广告的名称字段。|
| \_新的\_窗口打开\_ | 如果重定向\_url 指定的 URL 应在新窗口中打开，则返回 true。 |
| 重定向\_url| 用户将通过选择广告定向到的 URL。|

### <a name="ad-image-attributes"></a>Ad 映像属性

|Attribute   |描述   |
|---|---|
| 替换\_文本 | 返回要在标记的 alt 特性中显示的文本。 |
| height          | 返回图像的高度（以像素为单位）                             |
| 链接             | 返回图像的 URL 源。                                  |
| width           | 返回图像的宽度（以像素为单位）                              |


## <a name="blogs"></a>博客

提供访问和呈现博客和博客文章的功能。

博客对象允许您选择特定的博客或博客文章。

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

### <a name="blogs-object"></a>博客对象

博客对象允许您访问门户中的任何特定博客，或访问门户中的所有博客文章（无论使用哪种博客）。

下表说明了与博客对象相关联的属性。

|Attribute   |描述   |
|---|---|
| 创纪录               | 返回一个 blogposts 对象，该对象包含门户中的所有博客文章。     |
| \[博客名称或 id\] | 你可以通过其名称或 Id 属性访问任何博客。                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>博客对象

博客对象允许你使用单个博客，使你能够访问该博客的帖子。

下表说明了与博客对象关联的各种属性。

|Attribute   |描述   |
|---|---|
| 创纪录 | 返回一个 blogposts 对象，该对象包含博客的所有博客文章。 |
| 名称  | 博客的名称。                                              |
| 词首 | 博客的标题。                                             |
| 链接   | 博客的 URL。                                               |

### <a name="blogposts-object"></a>blogposts 对象

Blogposts 对象允许访问博客文章对象的集合。 除了使用液体过滤器外，还可以对博客文章进行排序并实现分页：

{% assign blogposts = blog\_"adx\_name"，"desc" | 分页：0，4 | all%}请注意，博客。所有文章也是获取所有博客文章博客的有效方法。文章 |from\_索引： 0 |take：还可以使用2个

下表说明了与 blogposts 对象关联的各种属性。

|Attribute   |描述   |
|---|---|
| 一切 | 返回集合中的所有 blogpost 对象 |

### <a name="blogpost-object"></a>blogpost 对象

指单个博客文章。

下表说明了与 blogpost 对象关联的各种属性。

|Attribute   |描述   |
|---|---|
| 链接            | 发布的 URL。                                                                |
| Content        | 返回帖子的内容字段。                                             |
| Content        | 返回帖子的内容字段。                                             |
| 主持         | 返回 post 的 authorf （只是 contact 实体对象）。          |
| 词首          | 帖子的标题。                                                              |
| 注释\_计数 | 返回给定 post 的注释数的整数值。 |
| 发布\_日期  | 发布发布的日期。                                           |

## <a name="entities"></a>条目

允许你按 ID 加载任何 PowerApps 实体。 如果实体存在，则将返回一个实体对象。 如果找不到具有给定 ID 的实体，则将返回[null](liquid-types.md#null) 。  

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

### <a name="entity"></a>本体

实体对象提供对 PowerApps 实体记录的属性的访问权限。


|             Attribute              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 ID                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    作为字符串的实体的 GUID ID。 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           逻辑\_名称            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   实体的 PowerApps 逻辑名称。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               说明                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             加载与实体关联的任何注释（批注），按从最旧到最新（event.manualintervention.createdon）的顺序排列。 注释作为注释对象返回。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            访问             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             加载实体的实体权限断言结果。 结果以权限对象的形式返回。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                链接                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    返回实体的 PowerApps 门户内容管理系统 URL 路径。 如果该实体在当前网站中没有有效的 URL，则返回 null。 通常，这只会返回已集成到门户 CMS 的某些实体类型的值，除非你已在应用程序中自定义了 URL 提供程序。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[属性或关系名称\] | 可以通过逻辑名称访问 PowerApps 实体的任何属性。 `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>大多数实体属性的值直接映射到[液体类型](liquid-types.md)：两个选项字段映射到布尔值，将文本字段映射到字符串，将数字/货币字段映射到数字，将日期/时间字段映射到日期对象。 但某些属性类型将作为对象返回：<ul><li>查找（实体引用）字段作为实体引用对象返回。</li><li>选项集/选择列表字段作为选项集值对象返回。</li><li>还可以按关系架构名称加载任何相关实体。</li>`{{ page.adx_webpage_entitylist.adx_name }}`如果关系为自反身（即自引用），则将返回反身关系对象。 （否则，结果将不明确。）`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**注意**：加载大量相关实体，或在单个模板中访问大量关系时，可能会对模板呈现性能产生负面影响。 避免在循环中为数组中的每个项加载相关实体。 如果可能，请使用[PowerApps common data service 实体标记](portals-entity-tags.md)来加载实体的集合。 |

### <a name="entity-reference"></a>实体引用

查找特性值作为实体引用对象返回，具有以下属性。


|   Attribute   |                                                描述                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      ID       | 作为字符串的被引用实体的 GUID ID。 <br> 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| 逻辑\_名称 |  被引用实体的 PowerApps 逻辑名称。   |
|     名称      |                           被引用实体的主要名称属性。                            |

### <a name="note"></a>纪录

注释是一个实体对象，它提供对注释记录的属性和关系的访问。 除了实体对象的所有属性，注释还具有以下其他属性。


|  Attribute   |                                                                                                                                                                                                                                  描述                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | 以 Base64 编码的字符串的形式加载便笺批注记录的 documentbody 特性。 由于此属性的内容可能很大，因此不会随便笺属性的其余部分一起加载，只需按需加载。 <br> **注意**： documentbody 属性的使用可能会对模板渲染性能产生负面影响，应慎用。<br>如果可能，请使用 url 属性提供指向注释附件的链接。 |
|     链接      |                                                                                                                                   返回内置门户批注附件处理程序的 URL 路径。 如果用户具有权限，并且该便笺包含附加文件，则对此 URL 的请求将下载注释文件附件。                                                                                                                                    |

>[!Note]
> [其他筛选器](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>选项集值

选项集/选择列表属性值以实体引用对象的形式返回，具有以下属性。

| Attribute | 描述                                                     |
|-----------|-----------------------------------------------------------------|
| 标签     | 选项集/选择列表属性值的本地化标签。 例如，Active|
| Value     | 选项集/选择列表属性值的整数值。 例如0                                                           |

### <a name="entity-permissions"></a>实体权限

实体权限对象提供对实体的聚合权限断言结果的访问。

| Attribute       | 描述                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 可以\_追加     | 如果当前用户有权将记录追加到此记录的关系，则返回 true。 否则，返回 false。                                                                                              |
| 可以\_追加\_到 | 如果当前用户有权将此记录附加到另一个实体的关系，则返回 true。 否则，返回 false。                                                                                      |
| 可以\_创建     | 如果当前用户有权创建此实体类型的新记录，则返回 true。 否则，返回 false。                                                                                                      |
| 可以\_删除     | 如果当前用户有删除此记录的权限，则返回 true。 否则，返回 false。                                                                                                                          |
| 可以\_读取       | 如果当前用户有权读取此记录，则返回 true。 否则，返回 false。                                                                                                                            |
| 可以\_写入      | 如果当前用户有权更新此记录，则返回 true。 否则，返回 false。                                                                                                                          |
| 存在的规则\_    | 如果由此对象表示的权限结果是显式定义的权限规则的结果，则返回 true。 如果默认值为 false，则返回 false，因为没有显式定义的权限。 |

### <a name="reflexive-relationship"></a>自反关系

尝试加载实体上的反身（即自引用）关系将返回具有以下属性的对象。

| Attribute     | 描述                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| 按反身\_ | 返回 true。 可用于测试由关系返回的对象是否为自反关系对象。 |
| 参阅    | 返回给定关系的引用实体的数组。                                           |
| 满足   | 返回给定关系的引用实体。 如果不存在引用实体，则返回 null。 如果关系为多对多（N：N），则返回引用实体的数组。                          

## <a name="entitylist"></a>entitylist

在[PowerApps common data service 实体标记](portals-entity-tags.md)中使用 entitylist 对象。 它提供对给定实体列表的所有属性的访问权限。  

> [!Note]                                                       
> [呈现与当前页关联的实体列表](render-entity-list-current-page.md)

### <a name="attributes"></a>特性

> [!Note]
> [条目](#entities)

|               Attribute               |                                                                                                                            描述                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            创建\_已启用            |                                                                                如果为实体列表配置了新记录，则返回 true。 否则，返回 false。                                                                                |
|              创建\_url              |                                                                                          返回实体列表的创建链接/按钮的已配置 URL 路径。                                                                                          |
|            \_启用详细信息            |                                                                         如果为实体列表配置了单个记录的详细信息视图，则返回 true。 否则，返回 false。                                                                          |
|         详细\_id\_参数         |               返回构造记录详细信息视图 URL 时用于记录 ID 的查询字符串参数名称。 有关使用液体过滤器来构造 Url 的详细信息，请参阅[URL 筛选器](liquid-filters.md#url-filters)。 例如，id                |
|             详细\_标签             |                                                                                     返回实体列表的详细信息视图链接/按钮的已配置本地化标签。                                                                                     |
|              详细信息\_url              |                                                                                       返回实体列表的详细信息视图链接/按钮的已配置 URL 路径。                                                                                        |
|           空\_列出\_文本           |                                                                                返回在实体列表视图未返回任何结果时要显示的已配置的本地化文本。                                                                                |
|      启用\_实体\_权限      |                                                                               如果为此实体列表启用了实体权限筛选，则返回 true。 否则，返回 false。                                                                               |
|         实体\_逻辑\_名称         |                                                 返回此实体列表要显示的记录的 PowerApps 实体逻辑名称。 例如，联系                                                 |
|   筛选\_帐户\_属性\_名称    |                                            返回将用于按当前门户用户的父帐户筛选结果记录的帐户查找的属性逻辑名称。 例如，accountid                                            |
|         筛选\_应用\_标签          |                                                            返回已配置的本地化标签，该标签用于将高级属性筛选器应用于实体列表结果的链接/按钮。                                                            |
|          筛选\_定义           |                      返回实体列表的 JSON 特性筛选器定义。 有关如何使用 metafilters 液体筛选器处理此定义的详细信息，请参阅[实体列表筛选器](liquid-filters.md#entity-list-filters)。                       |
|            筛选\_已启用            |                                                                               如果为实体列表启用了高级特性筛选，则返回 true。 否则，返回 false。                                                                               |
| 筛选\_门户\_用户\_属性\_名称 |                                                 返回用于联系人查找的属性的逻辑名称，该名称将用于按当前门户用户的联系人筛选结果记录。 例如，contactid                                                  |
|   筛选\_网站\_属性\_名称    |                                              返回 adx\_网站的查找的属性逻辑名称，该名称将用于筛选当前门户网站的结果记录。 例如，adx\_websiteid&gt                                              |
|            语言\_代码             |                                               返回 PowerApps 整数语言代码，该代码将用于选择此实体列表的所有本地化标签。                                                |
|              页面\_大小               |                                                                                                   返回实体列表的已配置结果页大小。                                                                                                    |
|          主\_密钥\_名称           |                                                                                  返回此实体列表要显示的记录的主键属性逻辑名称。                                                                                  |
|            已启用搜索\_            |                                                                                         如果为此实体列表启用了搜索，则返回 true。 否则，返回 false。                                                                                          |
|          搜索\_占位符          |                                                                                        返回为实体列表搜索字段占位符配置的本地化文本。                                                                                        |
|            搜索\_工具提示            |                                                                                             返回实体列表搜索工具提示的已配置本地化文本。                                                                                             |
|                 视图                 |                                                                                           返回实体列表的可用视图，作为实体列表视图对象。                                                                                           |
|      \[属性逻辑名称\]       | 您可以按逻辑名称访问实体列表（adx\_entitylist） PowerApps 记录的任何属性，与[实体](liquid-objects.md#entity)对象的方式相同。 例如，{{entitylist. adx\_名称}} |

### <a name="entity-list-view-attributes"></a>实体列表视图属性

|          Attribute          |                                                                                     描述                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           表列           |                                                         返回作为实体列表视图列对象的视图列。                                                         |
|    实体\_逻辑\_名称    |               为包含在视图中的记录返回 PowerApps 实体逻辑名称。 例如，联系                |
|             ID              |                                                                          返回视图的 GUID ID。                                                                           |
|       语言\_代码        | 返回 PowerApps 整数语言代码，该代码将用于选择视图的所有本地化标签（列标题等）。 |
|            名称             |                                          返回视图的 PowerApps 显示名称。                                          |
| 主\_密钥\_逻辑\_名称 |        为视图中包含的记录返回 PowerApps 实体主键逻辑名称。 例如，contactid         |
|      排序\_表达式       |                                               返回视图的默认排序表达式。 例如，name ASC，event.manualintervention.createdon DESC                                               |

### <a name="entity-list-view-column-attributes"></a>实体列表视图列特性

|    Attribute     |                                                                                    描述                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 特性\_类型  | 返回列的 PowerApps 属性类型名称，以字符串形式返回。 例如，Lookup，选择列表，String，Boolean，DateTime |
|  逻辑\_名称   |                       返回列的 PowerApps 属性逻辑名称。 例如，event.manualintervention.createdon                       |
|       名称       |                      返回列的本地化 PowerApps 显示名称。 例如，在上创建                       |
| 排序\_升序  |                                      返回按升序对列进行排序的排序表达式字符串。 例如，event.manualintervention.createdon ASC                                       |
| 排序\_降序 |                                     返回按降序对列进行排序的排序表达式字符串。 例如，event.manualintervention.createdon DESC                                      |
|  排序\_禁用  |                                                   如果对列禁用了排序，则返回 true。 否则，返回 false。                                                    |
|  排序\_启用   |                                                    如果为列启用了排序，则返回 true。 否则，返回 false。                                                    |
|      width       |                                                              返回为列配置的宽度（以像素为单位）。                                                              |

## <a name="entityview"></a>entityview

Entityview 对象用于 entityview 标记中，并提供对该视图的元数据的访问权限以及查看结果记录。

### <a name="attributes"></a>特性

|          Attribute          |                                                                               描述                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           表列           |                         返回视图中作为[实体视图列对象](liquid-objects.md#entity-list-view-column-attributes)的列。                          |
| \_拒绝实体\_权限  | 如果对查看结果的访问被拒绝，因为当前用户的实体权限不足，则返回 true。 如果已授予对查看结果的读取访问权限，则返回 false。 |
|    实体\_逻辑\_名称    |                   视图结果记录的 PowerApps 实体逻辑名称。 例如，联系                   |
|         第一个\_页面         |                 视图结果的第一页的页码。 除非未返回结果（在这种情况下，它将为 null），否则将为1。                  |
|             ID              |                            定义此 entityview 的 PowerApps 视图的 GUID ID。                             |
|       语言\_代码        |             用于为当前视图加载本地化标签的 PowerApps 整数语言代码。              |
|         最后\_页面          |                                 查看结果的最后一页的页码。 如果未返回任何结果，则此值为 null。                                  |
|            路径名             |              定义此 entityview 的 PowerApps 视图的名称，例如活动联系人。               |
|         下一\_页面          |                                下一页查看结果的页码。 如果没有下一页结果，则此值将为 null。                                 |
|            分页             |                                                           视图结果的当前页的页码。                                                           |
|            页            |                                          返回包含当前视图的所有结果页的页码数组。                                          |
|         页面\_大小          |                                                      当前视图每页返回的结果数。                                                       |
|       上一个\_页面        |                              下一页查看结果的页码。 如果没有以前的结果页，则将为 null。                               |
| 主\_密钥\_逻辑\_名称 |  此视图的结果实体的主键属性的 PowerApps 逻辑名称。 例如，contactid。   |
|           记录           |                                                   视图的当前结果记录页，作为实体对象。                                                    |
|      排序\_表达式       |                                             视图的默认排序表达式。 例如，nameASC，event.manualintervention.createdon DESC。                                              |
|        总\_页数         |                                                              视图的结果页的总数。                                                              |
|       \_记录总数        |                                                       视图的总结果数（跨所有页面）。                                                       |

## <a name="events"></a>事件

提供访问和呈现事件的能力。 Events 对象允许您选择特定事件或所有事件。

### <a name="events-object"></a>events 对象

Events 对象允许访问门户中的任何特定事件，或访问门户中的所有事件（无论事件如何）。

Events 对象具有以下属性：

|Attribute   |描述   |
|---|---|
|实例 |返回一个 eventoccurancessobject，其中包含门户中的所有事件 |
|[事件名称或 id] |可以通过名称或 Id 属性访问任何事件。<br>{% assign 事件 = 事件 [&quot;事件名称&quot;]%}<br>{% assign 事件 = events [&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;]%} |

### <a name="event-object"></a>事件对象

事件对象允许您使用单个事件，使您可以访问该事件的计划和发生次数。

事件对象具有以下属性：

|Attribute   |描述   |
|---|---|
| 次数 | 返回一个 eventoccurrencesobject，其中包含事件的所有匹配项。 |
| 路径名       | 事件的名称。                                                     |
| 链接        | 事件的 URL。                                                      |

### <a name="eventoccurences-object"></a>eventoccurences 对象

Eventoccurrences 对象允许访问事件发生对象的集合。 您可以对事件的出现顺序进行排序，并指定要检索的事件的日期范围，还可以使用液体过滤器来实现分页。

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

请注意，

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

也可能。

以下属性与 eventoccurrences 对象关联

|Attribute   |描述   |
|---|---|
| 一切 | 返回集合中的所有 eventoccurance 对象。 |

### <a name="eventoccurence-object"></a>eventoccurence 对象

表示一个事件发生。 下面给出了关联的属性：

|Attribute   |描述   |
|---|---|
| 链接                 | 出现位置的 URL。    |
| \_所有\_day\_事件 | 这是全天事件吗？     |
| 开始\_时间         | 事件的开始时间。 |
| 结束\_时间           | 事件的结束时间。   |


## <a name="forloop"></a>forloop

包含在 for 循环块中有用[的](iteration-tags.md#for)属性。  

> [!Note]
> forloop 只能在[for](iteration-tags.md#for)标记中使用。

**编写**

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

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| 1   | 如果它是循环的第一次迭代，则返回 true。 如果不是第一次迭代，则返回 false。       |
| 编入   | 当前项在集合中的位置，其中第一个项的位置为1。                   |
| index0  | 当前项在集合中的位置，其中第一个项的位置为0。                   |
| Last    | 如果它是循环的最后一个迭代，则返回 true。 如果不是最后一次迭代，则返回 false。         |
| 长短  | 返回循环的迭代次数，ߝ要循环访问的集合中项的数目。 |
| rindex  | 循环中的剩余项数（长度索引），其中1是最后一项的索引。              |
| rindex0 | 循环中的剩余项数（长度索引），其中0是最后一项的索引。              |


## <a name="forums"></a>论坛

提供访问和呈现论坛和论坛主题的能力。 请注意，使用液体呈现论坛数据的能力扩展到帖子，但若要创建新的 post 或线索，则必须使用 ASP.NET web 窗体页模板，其中内置了所述功能（如默认论坛主题和论坛帖子页面模板）。

论坛对象允许您选择论坛或论坛线程：

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

论坛对象允许您访问门户中的任何特定论坛，或访问门户中的所有论坛主题（无论论坛如何）。

利用论坛对象，您可以使用单个论坛，使您能够访问该论坛的线索。

Forumthreads 对象允许访问 forumthread 对象的集合。 您可以使用液体过滤器对论坛线索进行排序并实现分页。

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

单个论坛线索

Forumposts 对象允许访问 forumpost 对象的集合。

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| 线程              | 返回一个 forumthreads 对象，该对象包含门户中的所有 forumthread 对象。             |
| 一切                  | 返回门户中的所有论坛对象。 请注意，网站. 论坛也是等效的。    |
| 线程\_计数        | 返回整个网站中有多少线程数的整数值。 |
| post\_计数          | 返回门户中张贴内容总数的整数值。                       |
| \[论坛名称或 id\] | 可以按名称或 Id 属性访问任何论坛。 <br>"{% 分配论坛 = 论坛 [论坛名称]%}<br>{% 分配论坛 = 论坛 [da8b8a92-2ee6-476f-8a21-782b047ff460]%} 

### <a name="forum-object"></a>论坛对象

### <a name="attributes"></a>特性

> [!Note]
> [条目](#entities)

|Attribute   |描述   |
|---|---|
| 线程       | 返回一个 forumthreads 对象，该对象包含论坛的所有论坛主题。               |
| 名称          | 论坛的名称。                                                                  |
| 线程\_计数 | 返回论坛中有多少线程数的整数值。      |
| post\_计数   | 返回整个论坛中有多少帖子的计数的整数值。 |

### <a name="forumthreads-object"></a>forumthreads 对象

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| 一切 | 返回集合中的所有 forumthread 对象。 |

### <a name="forumthread-object"></a>forumthread 对象

### <a name="attributes"></a>特性

> [!Note]
> [条目](#entities)

|Attribute   |描述   |
|---|---|
| 创纪录        | 返回一个 forumposts 对象，该对象包含线程的所有论坛帖子。            |
| 主持       | 返回线程的作者（只是联系人实体对象）。      |
| 最新\_发布 | 返回线程中的最新帖子。                                            |
| 第一\_post  | 返回线程中的第一个 post。                                             |
| post\_计数  | 返回线程中有多少个 post 的计数的整数值。 |
| \_应答 | 线程是否已应答？                                                    |
| \_粘滞   | 线程是否为粘滞线程？                                                    |

### <a name="forumposts-object"></a>forumposts 对象

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| 一切 | 返回集合中的所有 forumthread 对象。 |

单个论坛帖子

### <a name="attributes"></a>特性

> [!Note] 
> [条目](#entities)

|Attribute   |描述   |
|---|---|
| 主持     | 返回帖子的作者（只是联系人实体对象）。 |
| Content    | 帖子的内容。                                                   |
| \_应答 | 这是否会向线程发送答案？                                      |


## <a name="knowledge"></a>知道

提供对 PowerApps knowledgearticle 和类别实体记录的访问权限，以便在门户中呈现项目和类别。

### <a name="attributes"></a>特性

|Attribute|描述|
|---|---|
|文章|返回一个项目对象，该对象包含门户中可用的 knowledgearticle 实体记录的项目对象。|
|类型|返回一个 category 对象，其中包含门户中可用的类别实体记录的类别对象。|
|||

### <a name="articles-object"></a>项目对象

项目对象允许您访问项目对象的集合。 您可以使用液体过滤器对文章进行排序并实现分页。

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

### <a name="attributes"></a>特性

|Attribute|描述|
|---|---|
|种 |返回包含大多数视图的项目对象的集合。 `{% assign popular_articles = knowledge.articles.popular %}` |
|新 |返回包含最新修改日期的项目对象的集合。 `{% assign recent_articles = knowledge.articles.recent %}` |
|top |返回包含最高评级的项目对象的集合。 `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>筛选

以下筛选器可以接受页面大小和语言的可选参数。 第一个参数是要检索的一个或多个记录。 默认页面大小为5。 第二个参数是语言的代码，用于检索给定语言的文章。 筛选器可以与其他[液体过滤器](liquid-filters.md)结合。

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|Attribute|描述|
|---|---|
|种 |返回包含大多数视图的项目对象的集合。 `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|新 |返回包含最新修改日期的项目对象的集合。 `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|top |返回包含最高评级的项目对象的集合。 `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>类别对象

Category 对象允许访问 category 对象的集合。 您可以使用液体过滤器对类别进行排序并实现分页。

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

### <a name="attributes"></a>特性

|Attribute|描述|
|---|---|
|新 |返回类别对象的集合，这些对象包含最新的修改日期。 |
|top_level |返回不具有父类别的 category 对象的集合。 |
|||

### <a name="filters"></a>筛选

以下筛选器可以接受指示页面大小的可选参数。 默认页面大小为5。 筛选器可以与其他[液体过滤器](liquid-filters.md)结合。

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|Attribute|描述|
|---|---|
|新 |返回类别对象的集合，这些对象包含最新的修改日期。 可以提供参数 `{% assign recent_categories = knowledge.categories \| recent: 10 %}` |
|top_level |返回不具有父类别的 category 对象的集合。 `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>项目对象

项目对象允许你使用单个 knowledgearticle，在门户中显示该文章的详细信息。

### <a name="attributes"></a>特性

除了下面列出的属性外，项目是[实体](#entity)对象。

|Attribute|描述|
|---|---|
|article_public_number| 文章的公开页码。|
|comment_count| 给定项目的注释数的整数值。|
|Content|项目的内容。|
|current_user_can_comment|返回一个布尔值，该值指示当前用户是否可以在项目中添加注释。|
|is_rating_enabled|返回一个布尔值，该值指示是否启用项目评级。|
|字|项目中的关键字。|
|路径名|项目标题的备用别名。|
|定额|项目的小数级别值。|
|词首|项目的标题。|
|view_count|查看项目的次数的整数值。|
|||

### <a name="category-object"></a>category 对象

Category 对象允许你使用单个类别在门户中显示其详细信息。

### <a name="attributes"></a>特性

除了下面列出的属性，类别还是一个[实体](#entity)对象，具有所有相同属性。

|Attribute|描述|
|---|---|
|categorynumber|类别的类别号。|
|路径名|类别标题的备用别名。|
|词首|类别的标题。|
|||

## <a name="page"></a>分页

引用当前门户请求页。 此对象将[站点地图](#sitemap)和当前请求[实体](#entities)（通常为网页）的属性组合在一起。  

Page 对象提供对当前页的痕迹导航、当前页的标题或 URL 以及基础 PowerApps 记录的任何其他属性或相关实体的访问权限。

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
> [条目](#entities)

|             Attribute              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            痕迹导航             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 返回页面的痕迹导航站点地图对象，从站点地图根节点开始，到父节点结束。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              观看              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 返回页面的子站点地图节点对象。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               上层               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           返回页面的父站点地图节点。 如果该页是主页，则父页将为 null。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               词首                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                页面的标题。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                链接                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 页的 URL。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[属性或关系名称\] | 可以通过逻辑名称访问页的基础 PowerApps 记录的任何属性。<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>大多数实体属性的值直接映射到[液体类型](liquid-types.md)：两个选项字段映射到布尔值，将文本字段映射到字符串，将数字/货币字段映射到数字，将日期/时间字段映射到日期对象。 但某些属性类型将作为对象返回：<ul><li>查找（实体引用）字段作为[实体引用对象](#entity-reference)返回。</li><li>选项集/选择列表字段作为[选项集值对象](#option-set-value)返回。</li> 还可以按关系架构名称加载任何相关实体。 <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>如果关系为反身（即自引用），则将返回[实体](#entities)对象。 （否则，结果将不明确。）`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**注意**：加载大量相关实体，或在单个模板中访问大量关系时，可能会对模板呈现性能产生负面影响。 避免在循环中为数组中的每个项加载相关实体。 如果可能，请优先使用[PowerApps common data service 实体标记](portals-entity-tags.md)来加载实体的集合。 |

## <a name="polls"></a>调查

提供访问和呈现轮询的能力。

投票对象允许您选择特定的轮询或轮询位置：

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

### <a name="polls-attributes"></a>投票特性

|Attribute   |描述   |
|---|---|
| 布置          | 返回 pollplacements 对象。                                      |
| \[轮询名称或 id\] | 您可以按名称或 Id 属性访问任何轮询。 `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>投票位置属性

|Attribute   |描述   |
|---|---|
| \[轮询位置名称或 id\] | 可以按名称或 Id 属性访问任何轮询位置。`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>投票位置属性

> [!Note] 
> [条目](#entities)                                       

|Attribute   |描述   |
|---|---|
| 名称           | 返回轮询位置的名称字段。                            
| 放置\_url | 可用于检索模板完全呈现的轮询位置的 URL。                       |
| 调查          | 返回与放置关联的投票对象的集合。 [迭代标记](iteration-tags.md)和[数组筛选器](liquid-filters.md#array-filters)可用于此集合。  |  
| 随机\_url    | 可用于从模板完全呈现的位置中检索随机轮询的 URL。         |
| 提交\_url    | 已完成的轮询提交到的 URL。                                                             |

### <a name="poll-attributes"></a>投票特性

> [!Note] 
> [条目](#entities)                                          

|Attribute   |描述   |
|---|---|
| \_用户\_投票       | 如果当前用户（已登录或匿名）已在此轮询中投票，则返回 true。         |
| 名称                   | 返回轮询的名称字段。                                                              |
| 选项                | 返回与投票关联的轮询选项对象的集合。 [迭代标记](iteration-tags.md)和[实体](#entities)可用于此集合。  |  
| 轮询\_url              | 可用于检索模板完全呈现的轮询的 URL。                       |
| 问               | 返回用于轮询的 "问题" 字段。                                                          |
| \_标签提交\_按钮  | 返回一个字符串，该字符串可用于覆盖轮询的提交按钮标签。               |
| 提交\_url            | 已完成的轮询提交到的 URL。                                                   |
| 用户\_选定\_选项 | 返回用户选择的 polloption 对象（如果已对其进行了投票）。                  |
| 投票                  | 返回已按表格进行投票的投票数。                                |

### <a name="poll-option-attributes"></a>轮询选项属性

>[!Note]
> [条目](#entities)                                         

|Attribute   |描述   |
|---|---|
| 答案     | 返回轮询的 "答案" 字段。 |
| 一定 | 将选项的轮询中的投票百分比返回为从0到100的小数。 |
| 投票      | 返回已为选项按表格方式列出的投票数。                              |


## <a name="request"></a>需要

包含当前 HTTP 请求的相关信息。

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> 可以通过使用 URL 筛选器在液体中动态生成 Url。 

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| params           | 当前请求的命名参数值。 params 是 URL 查询字符串参数、窗体发布参数和 cookie 的组合。  |
| 通道             | 当前请求 URL 的路径。 <br> /profile|
| 路径\_和\_查询 | 当前请求 URL 的路径和查询。<br> /profile/？ foo = 1 & bar = 内容|
| query            | 当前请求 URL 的查询部分。 <br> ？ foo = 1 & bar = 内容 |
| 链接              | 当前请求的完整 URL。<br>  http://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>searchindex

Searchindex 对象用于[PowerApps common data service 实体标记](portals-entity-tags.md)中，并提供对查询结果的访问。  

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

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| 近似\_\_命中总数 | 返回与索引查询匹配的总命中数的近似值。 请注意，由于搜索索引适用于安全筛选和其他设计因素，此数字只是近似值，可能与在某些情况下可用于当前用户的结果总数不完全匹配。  |
| 分页                     | 返回当前查询的页码。                                                                                                                                                                                                           |
| 页面\_大小               | 返回当前查询的最大页面大小。 请注意，如果想要为当前页面返回的实际结果数（因为这可能小于指定的最大页面大小），请使用 "结果"。大小。                                                                                           |
| 后果                  | 返回作为搜索索引结果对象的查询结果页。                                                                                                                                                                                          |

### <a name="search-index-results"></a>搜索索引结果

|   Attribute   |                                                                                                                                                描述                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    本体     |                                                                                                                            结果的基础[实体](#entities)。                                                                                                                            |
|   代码    | 结果的相关简短文本片段，其中包含与指定查询匹配的术语，并使用 &lt;em&gt; HTML 标记突出显示。 请注意，某些类型的查询不支持突出显示的片段，如模糊查询（~）和通配符查询（\*）。 在这些情况下，此属性将为 null。 |
|      ID       |                                                             结果的基础记录的 PowerApps 实体 ID （以字符串形式表示）。 例如，936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| 逻辑\_名称 |                                                                           结果的基础记录的 PowerApps 实体逻辑名称。 例如，adx\_网页                                                                           |
|    number     |                                                            从1开始，在所有结果页中的结果数。 例如，对于第二页结果的第一个结果，页大小为10，此值将为11。                                                             |
|     分值     |                                                                                                 作为浮点值的结果的 Lucene 分数。 将返回按此值排序的结果。                                                                                                 |
|     词首     |                                                                                                                                          结果的标题。                                                                                                                                          |
|      链接      |                                                            结果的 URL。 这通常&mdash;，但不一定&mdash;为当前应用程序的绝对路径，而不是完整的 URL。 例如：/articles/article1/                                                             |

## <a name="settings"></a>设置

允许按名称加载任何[站点设置](../configure/configure-site-settings.md)。 如果找不到具有给定名称的设置，则将返回[null](liquid-types.md#null) 。  

> [!Note]
> 设置作为[字符串](liquid-types.md#string)返回，但你可以使用[类型筛选器](liquid-filters.md#type-filters)将它们转换为其他类型。

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
> [呈现网站页眉和主导航栏](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>站点地图

允许访问门户网站图。

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

|Attribute   |描述   |
|---|---|
| 当前 | 返回当前页的站点地图节点对象。                    |
| Root    | 返回网站的根（主页）页的站点地图节点对象。 |

### <a name="site-map-node-attributes"></a>站点地图节点属性

|Attribute   |描述   |
|-------|-------|
| 痕迹导航           | 返回节点的痕迹导航站点地图对象，从站点地图根节点开始，到父节点结束。 |
| 观看              | 返回节点的子站点地图节点对象。                                                                  |
| 描述           | 节点的说明/摘要内容。 （此字段可能包含 HTML。）                                          |
| 本体                | 返回节点的基础[实体](#entities)。 如果该节点没有基础实体，则此值将为 null。                                                         |
| \_站点地图\_祖先 | 如果站点地图节点是当前节点的上级，则返回 true; 否则返回 false。                                                                                                         |
| \_站点地图\_当前  | 如果站点地图节点是当前节点，则返回 true; 否则返回 false。                                                                                                         |
| 上层                | 返回节点的父站点地图节点。 如果节点是根节点，则父节点将为 null。                                                                     |
| 标题                 | 节点的标题。                                                                                                |
| 链接                   | 节点的 URL。                                                                                                  |


## <a name="sitemarkers"></a>sitemarkers

允许按名称加载任何站点标记。 如果 sitemarker 存在，则将返回 sitemarker 对象。 如果找不到具有给定名称的 sitemarker，则将返回[null](liquid-types.md#null) 。  

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
> [呈现网站页眉和主导航栏](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>Sitemarker 特性

|         Attribute          |                                                                                    描述                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            链接             |                                                                         Sitemarker 目标的 URL。                                                                         |
| \[属性逻辑名称\] | 可以按逻辑名称访问 sitemarker 目标 PowerApps 记录的任何属性。 例如，{{sitemarker. adx\_名称}} |

## <a name="snippets"></a>片段

允许按名称加载任何内容片段。 如果找不到具有给定名称的代码段，则将返回[null](liquid-types.md#null) 。  

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
> tablerowloop 只能在[迭代标记](iteration-tags.md)标记中使用。

### <a name="attributes"></a>特性

|Attribute   |描述   |
|---|---|
| Col        | 返回当前行的索引（从1开始）。                                                       |
| col0       | 返回当前行的索引（从0开始）。                                                       |
| 列\_首先 | 如果当前列是行中的第一列，则返回 true; 否则，返回 false。               |
| 列\_上次  | 如果当前列是行中的最后一列，则返回 true; 否则，返回 false。                |
| First      | 如果它是循环的第一次迭代，则返回 true。 如果不是第一次迭代，则返回 false。       |
| 编入      | 当前项在集合中的位置，其中第一个项的位置为1。                   |
| index0     | 当前项在集合中的位置，其中第一个项的位置为0。                   |
| Last       | 如果它是循环的最后一个迭代，则返回 true。 如果不是最后一次迭代，则返回 false。         |
| 长短     | 返回循环的迭代次数，ߝ要循环访问的集合中项的数目。 |
| rindex     | 循环中的剩余项数（长度索引），其中1是最后一项的索引。              |
| rindex0    | 循环中的剩余项数（长度索引），其中0是最后一项的索引。              |



## <a name="user"></a>用户

指当前门户用户，允许访问基础 PowerApps 联系人记录的所有属性。 如果没有用户登录，则此变量将为[null](liquid-types.md#null)。  

user 是[实体](#entity)对象。  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>特性

除了具有[实体](#entity)对象的所有属性外，用户还具有以下属性。


|    Attribute     |                                                                                                                                                                                     描述                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      作用       |                                                      以[数组](liquid-types.md#array)的形式返回该用户所属的角色。<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**注意**：你还可以使用 `has_role` 筛选器来测试各个角色成员身份。                                                       |
| basic_badges_url | 返回用于检索用户徽章的服务 url。<br>若要呈现用户的徽章，你必须包含一个具有 "数据徽章" 和 "数据 uri" 属性的标记。 呈现当前用户的徽章：<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>按 id （变量 userid）来呈现用户的徽章：<br>\`< div 数据-标记数据-uri = "{{basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>weblinks

允许你按名称或 ID 加载任何 weblinks。  

如果 web 链接集存在，则将返回一个[web 链接集对象](#web-link-set-attributes)。 如果找不到具有给定名称或 ID 的 web 链接集，将返回[null](liquid-types.md#null) 。


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
> [呈现网站页眉和主导航栏](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Web 链接集特性

> [!Note]
> 除了下面列出的属性外，web 链接集是一个[实体](#entity)对象，具有所有相同属性。                                         

|         Attribute          |                                                                                 描述                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            复本            |                                                                      Web 链接集的 HTML 副本。                                                                      |
|            名称            |                                                                        Web 链接集的名称。                                                                         |
|           标题            |                                                                        Web 链接集的标题。                                                                        |
|          weblinks          |                                                       与 web 链接集关联的 web 链接对象的数组。                                                        |
| \[属性逻辑名称\] | 可以通过逻辑名称访问 web 链接集 PowerApps 记录的任何属性。 例如，{{weblinkset}} |

### <a name="web-link-attributes"></a>Web 链接属性

> [!Note]
> 除了下面列出的属性外，web 链接还是一个具有所有相同属性的[实体](#entity)对象。

|          Attribute          |                                                                              描述                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         描述         |                                                                 Web 链接的 HTML 说明。                                                                 |
|    仅显示\_\_图像     |                              布尔值属性，指示 web 链接是否应仅显示为图像，不显示链接文本。                               |
| 显示\_页面\_子\_链接 |            布尔值属性，指示 web 链接是否应显示指向链接页的[*站点地图*](#sitemap)子页面的链接（作为子链接）。             |
|            图像            |                                     此链接的 web 链接图像对象。 如果没有图像，则此属性将为 null。                                      |
|        \_外部         |                 布尔值属性，指示 web 链接的目标 URL 是否为外部站点（而不是内部门户页）。                  |
|    \_站点地图\_祖先    |                                如果 weblink 的 URL 引用当前站点地图节点的上级，则返回 true，否则返回 false。                                 |
|    \_站点地图\_当前     |                                        如果 weblink 的 URL 引用当前站点地图节点，则返回 true，否则返回 false。                                        |
|            名称             |                                                                    Web 链接的名称/标题。                                                                    |
|          Nofollow           |                                         布尔值属性，指示是否应将 web 链接标记为 rel = nofollow。                                         |
|    \_新的\_窗口打开\_    |                             布尔值属性，指示是否应在新的浏览器窗口中打开 web 链接（如果选中）。                             |
|           提示           |                                                                    Web 链接的工具提示文本。                                                                     |
|             链接             |                                                                       Web 链接的 URL。                                                                        |
|          weblinks           |                                                   与 web 链接关联的子 web 链接对象的数组。                                                   |
| \[属性逻辑名称\]  | 可以按逻辑名称访问 web 链接 PowerApps 记录的任何属性。 例如，{{weblink}} |

### <a name="web-link-image-attributes"></a>Web 链接图像属性

| 替换\_文本 | 图像的替换文字。                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| Height          | 包含图像的指定高度的整数。 如果未提供高度值，则此属性将为 null。 |
| 链接             | 图像的 URL。                                                                                               |
| 宽度           | 包含图像的指定宽度的整数。 如果未提供宽度值，则此属性将为 null。   |


## <a name="website"></a>网站

指门户网站，允许访问门户的 PowerApps 网站（adx\_网站）记录的所有属性。  

> [!Note]
> 网站是具有所有相同属性的[实体](#entity)对象。

**编写**

```
{{ website.adx_name }} ({{ website.id }})
```

**输出**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>另请参阅

[液体类型](liquid-types.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md)  
