---
title: 为门户使用 PowerApps Common Data Service 实体标记 |MicrosoftDocs
description: 了解 PowerApps Common Data Service 在门户中可用的实体标记。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6efc3e176602d366315b9b54b66593005051e55
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543265"
---
# <a name="powerapps-common-data-service-entity-tags"></a>PowerApps Common Data Service 实体标记

PowerApps 实体标记用于加载和显示 PowerApps 数据，或使用其他 PowerApps 门户框架服务。 这些标记是针对液体语言的 PowerApps 特定的扩展。

## <a name="chart"></a>流程图

将 PowerApps 图表添加到网页。 图表标记可以添加到网页上的 "复制" 字段中，也可以添加到 Web 模板的 "源" 字段中。 有关将 PowerApps 图表添加到网页的步骤，请参阅[在门户中将图表添加到](../configure/add-chart.md)网页。

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>参数

有两个用于图表标记的参数：图表 id 和 viewid。

**图表 id**

图表的可视化效果 ID。 可以通过导出图表获取此。

**viewid**

实体在视图编辑器中打开时的 ID。 

## <a name="powerbi"></a>powerbi

将 Power BI 的仪表板和报表添加到页面中。 标记可以添加到网页上的 "**复制**" 字段中，也可以添加到 web 模板的 "**源**" 字段中。 有关将 Power BI 报表或仪表板添加到门户中的网页的步骤，请参阅[在门户中将 Power BI 报表或仪表板添加到网页](../admin/add-powerbi-report.md)。

> [!NOTE]
> 要使标记正常工作，必须启用从 PowerApps 门户管理中心[Power BI 集成](../admin/set-up-power-bi-integration.md)。 如果未启用 Power BI 集成，则不会显示仪表板或报表。

### <a name="parameters"></a>参数

Powerbi 标记接受以下参数：

**通道**

Power BI 报表或仪表板的路径。 如果 Power BI 报表或仪表板是安全的，则必须提供身份验证类型。

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Power BI 报表或仪表板所需的身份验证类型。 此参数的有效值为：

- **匿名**：允许你将 "发布到 web Power BI 报表" 嵌入。 默认的身份验证类型为 Anonymous。

- **AAD**：允许您共享安全 Power BI 报表或仪表板，以便 Power BI Azure Active Directory 身份验证的用户。

- **powerbiembedded**：允许将安全 Power BI 报表或仪表板共享给没有 Power BI 许可证或 Azure Active Directory 身份验证设置的外部用户。 有关 Power BI Embedded 服务设置的信息，请参阅[Enable Power BI Embedded service](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)。 

添加 secure Power BI 报表或仪表板时，请确保它与门户 Azure Active Directory 或 Power BI Embedded 服务共享。 

> [!NOTE]
> `authentication_type` 参数的值不区分大小写。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

您还可以对一个或多个值筛选报表。 用于筛选报表的语法为：

URL？ filter =**Table**/**字段**eq '**value**'

例如，假设您想要筛选报表以查看名为 "经理 bert" 的联系人的数据。 必须将 URL 追加到以下内容：

？ filter = Executive/Executive eq ' 经理 bert 头发 '

完整的代码将是：

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

有关筛选报表的详细信息：[使用 URL 中的查询字符串参数筛选报表](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> 匿名报表不支持筛选。 

还可以通过使用 `capture ` 液变量来创建动态路径，如下所示：

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

关于液体变量的详细信息：[变量标记](variable-tags.md)

**tileid**

显示仪表板的指定图块。 必须提供磁贴的 ID。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**作用**

分配给 Power BI 报表的角色。 仅当**authentication_type**参数设置为**powerbiembedded**时，此参数才有效。

如果在 Power BI 中定义了角色并将其分配给了报表，则必须在**powerbi**液体标记中指定适当的角色。 角色允许您筛选要在报表中显示的数据。 可以指定用逗号分隔的多个角色。 有关在 Power BI 中定义角色的详细信息，请参阅[具有 Power BI 的行级别安全性（RLS）](https://docs.microsoft.com/power-bi/service-admin-rls)。

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

如果已将角色分配到 Power BI 报表，但没有在液体标记中指定**roles**参数或未在参数中指定角色，则会显示错误。

> [!TIP]
> 如果要使用门户中定义的 web 角色作为 Power BI 角色，可以定义一个变量并向其分配 web 角色。 然后，您可以在液体标记中使用已定义的变量。
>
> 假设你已将两个 web 角色定义为门户中的 Region_East 和 Region_West。 你可以使用以下代码来联接它们： `{% assign webroles = user.roles | join: ", " %}`
>
> 在上面的代码段中，`webroles` 是一个变量，并将 Region_East 和 Region_West web 角色存储在其中。
>
> 在液体标记中使用 `webroles` 变量：
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>不可

对于对该对象具有内容编辑权限的用户，可在门户上将给定 PowerApps 门户 CMS 对象呈现为可编辑。 可编辑对象包括[页面](liquid-objects.md#page)、[代码段](liquid-objects.md#snippets)和[weblinks](liquid-objects.md#weblinks)。  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>参数

向可编辑提供的第一个参数是可编辑的对象。 例如，这可以是 web 链接集、代码段或当前页面。 可选的第二个参数是指定要呈现和编辑的对象中的属性名称或键。 例如，这可能是实体属性的名称或代码段名称。

在这些初始参数之后，标记支持多个可选的命名参数。

**班级**

指定由此标记呈现的根元素的类特性值。

**缺省值**

如果可编辑的项没有值，则为要呈现的默认值。

**esc**

一个布尔值，指示由此标记呈现的值是否将经过 HTML 编码。 默认情况下，此值为 false。

**输送**

一个布尔值，指示是否将处理此标记呈现的文本值中的任何液体模板代码。 默认情况下，此值为 true。

**符**

此标记将呈现的容器 HTML 标记的名称。 默认情况下，此标记将呈现 div 元素。 通常建议你在 div 或 span 之间选择作为此参数的值。

**词首**

为内容编辑界面中的此可编辑项指定标签。 如果未提供任何内容，则将自动生成友好标签。

**类别**

一个字符串值，指示要显示的编辑接口的类型（适用于可编辑的文本值）。 此参数的有效值为 html 或 text。 html 为默认值。

## <a name="entitylist"></a>entitylist

按名称或 ID 加载给定的实体列表。 然后，可以使用将在标记块中使用的[entitylist 对象](liquid-objects.md#entitylist)访问实体列表的属性。 若要呈现实体列表的实际结果记录，请使用块中的[entityview](#entityview)标记。  

如果成功加载实体列表，则将呈现块中的内容。 如果找不到实体列表，则不会呈现块内容。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
默认情况下，entitylist 对象将被赋予变量 name entitylist。 还可以提供其他变量名。

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>参数

仅提供 "id"、"名称" 或 "键" 中的**一个**，以选择要加载的实体列表。

**识别**

按[GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) ID 加载实体列表。 id 必须是可分析为 GUID 的字符串。  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

通常，不会使用文本 GUID 字符串。 相反，id 将使用另一个变量的 GUID 属性来指定。

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**路径名**

按名称加载实体列表。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**按键**

按 ID**或**名称加载实体列表。 如果提供的密钥值可以分析为[GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier)，则会按 ID 加载实体列表。 否则，它将按名称加载。

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**语言\_代码**

用于选择要加载的实体列表本地化标签的 PowerApps 整数语言代码。 如果未提供任何语言\_代码，则将使用门户应用程序 PowerApps 连接的默认语言。

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

按名称或 ID 加载给定的 PowerApps 视图。 然后，可以使用将在标记块内提供的[entityview 对象](liquid-objects.md#entityview)来访问视图ߝ视图列元数据的属性、分页的结果记录等。  

如果成功加载视图，则将呈现块中的内容。 如果找不到该视图，则不会呈现块内容。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

默认情况下，entityview 对象将被赋予变量 name entityview。 还可以提供其他变量名。

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

如果 entityview 嵌套在 entitylist 块中，它将从实体列表继承其默认配置（结果页面大小、筛选器选项等）。 如果未向 entityview 提供任何视图 id 或名称参数，则将从封闭 entitylist 加载默认视图。

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>参数

提供**id** **或**逻辑\_名称，以选择要加载的 PowerApps 视图。 如果两者都未提供，并且 entityview 标记嵌套在 entitylist 标记中，则将加载封闭 entitylist 的默认视图。

**识别**

id 必须是可分析为 GUID 的字符串。

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

通常，不会使用文本 GUID 字符串。 相反，id 将使用另一个变量的 GUID 属性来指定。

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**逻辑\_名称**

要加载的视图的 PowerApps 实体逻辑名称。 必须与 name 结合使用。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**路径名**

要加载的视图的 PowerApps 名称。 必须与逻辑\_名称结合使用。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**筛选器**

指定是否按用户或帐户筛选视图结果。 必须具有用户或帐户的字符串值。

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

指定用于筛选视图结果的实体列表元数据筛选器表达式。 仅当 entityview 与 entitylist 结合使用时，此参数才有效。 在大多数情况下，此参数是根据[请求](liquid-objects.md#request)设置的。  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**为了**

指定用于排序视图结果的排序表达式。 排序表达式可以包含一个或多个实体属性逻辑名称，后跟 ASC 或 DESC 的排序方向。

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**分页**

指定要加载的视图结果页。 如果未指定此参数，则将加载结果的第一页。

此参数必须是整数值或可分析为整数的字符串。 如果为此参数提供了一个值，但该值为 null，或者不能将其分析为整数，则将加载结果的第一页。

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**页面\_大小**

指定要为当前结果页加载的结果数。 如果没有为此参数提供值，并且 entityview 在[entitylist](#entitylist)块中使用，则将使用实体列表页大小。 如果不在 entitylist 块中，将使用默认值10。

此参数必须是整数值或可分析为整数的字符串。 如果为此参数提供了一个值，但该值为 null，或者不能将其分析为整数，将使用默认页面大小。

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**寻找**

指定筛选视图结果的搜索表达式。 简单关键字搜索表达式将根据属性是否以关键字开头来进行筛选。 还可以在表达式中包含通配符 \*。

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数，以便可以基于用户输入设置搜索筛选器。  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**启用\_实体\_权限**

指定是否对视图结果应用实体权限筛选。 默认情况下，此参数设置为 false。 如果在 entitylist 块中使用 entityview，则此参数的值将从实体列表配置继承。

此参数必须为[布尔](liquid-types.md#boolean)值或可分析为布尔值的字符串（true、false）。 如果为此参数提供了一个值，但该值为 null，或者不能将其分析为布尔值，则将使用默认值 false。  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**语言\_代码**

PowerApps 整数语言代码，用于选择要加载的实体视图本地化标签（列标题标签等）。 如果未提供任何语言\_代码，则将使用门户应用程序 PowerApps 连接的默认语言。

如果在 entitylist 块中使用 entityview，则 entityview 将从 entitylist 继承其语言代码配置。

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

针对门户搜索索引执行查询。 然后，可以使用将在标记块内可用的[searchindex](liquid-objects.md#searchindex)访问匹配结果。  

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

默认情况下，将为搜索索引对象指定变量名称 searchindex。 还可以提供其他变量名。

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>参数

Searchindex 标记接受以下参数。

**query**

用于匹配结果的查询。 此参数用于接受索引查询的用户指定部分（如果有）。

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

此参数支持[Lucene 查询分析器语法](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)。

**筛选器**

用于匹配结果的附加查询。 如果需要，此参数旨在接受开发人员指定的结果筛选器。

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

此参数支持[Lucene 查询分析器语法](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)。  

> [!Note]     
> 筛选器与查询之间的区别在于，虽然这两种方法都将接受 Lucene 查询分析器语法，但查询旨在更包容性地分析此语法如何ߝ，因为大多数最终用户都不知道此语法。 因此，根据此语法分析查询失败，整个查询将被转义并作为查询文本提交。 另一方面，将严格分析筛选器，如果语法无效，则会返回错误。

**逻辑\_名称**

匹配结果将被限制为的 PowerApps 实体逻辑名称（以逗号分隔的字符串形式）。 如果未提供，则将返回所有匹配的实体。

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**分页**

要返回的搜索结果页。 如果未提供，则返回第一页（1）。

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

常见的用例是根据[请求](liquid-objects.md#request)设置此参数。  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**页面\_大小**

要返回的结果页的大小。 如果未提供，则将使用默认大小10。

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

按名称或 ID 完全呈现 PowerApps 配置的实体窗体。  

> [!Note]
> Entityform 标记仅可用于在基于 <em>[web 模板](store-content-web-templates.md)</em>的页面模板中呈现的内容。 尝试在基于重写的页模板内使用标记将不会呈现任何内容。 每页只能呈现一个 entityform 或 webform 标记。 entityform 或 webform 标记将不会呈现第一个标记。       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>参数

**路径名**

要加载的实体窗体的名称。

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**webform**

按名称或 ID 完全呈现 PowerApps 配置的 web 窗体。 Webform 标记仅可用于在基于[web 模板](store-content-web-templates.md)的页面模板中呈现的内容。 尝试在基于重写的页模板内使用标记将不会呈现任何内容。 每页只能呈现一个 entityform 或 webform 标记。 entityform 或 webform 标记将不会呈现第一个标记。                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>参数

**路径名**

要加载的 Web 窗体的名称。

`{% webform name:My Web Form %}`

### <a name="see-also"></a>另请参阅

[控制流标记](control-flow-tags.md)<br>
[迭代标记](iteration-tags.md)<br>
[变量标记](variable-tags.md)<br>
[模板标记](template-tags.md)
