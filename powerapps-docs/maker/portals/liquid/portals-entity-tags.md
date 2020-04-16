---
title: 为门户使用 Power Apps Common Data Service 实体标记 | MicrosoftDocs
description: 了解门户中的可用 Power Apps Common Data Service 实体标记。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/28/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 83247403a482f7ce980f83a5813be2fd158e1be0
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125649"
---
# <a name="power-apps-common-data-service-entity-tags"></a>Power Apps Common Data Service 实体标记

Power Apps 实体标记用于加载和显示 Power Apps 数据，或使用其他 Power Apps 门户框架服务。 这些标记是 Power Apps 特定的 Liquid 语言扩展。

## <a name="chart"></a>图表

向网页添加 Power Apps 图表。 可在网页中的“复制”字段内或 Web 模板中的“源”字段内添加图表标记。 有关向网页添加 Power Apps 图表的步骤，请参阅[向门户中的网页添加图表](../configure/add-chart.md)。

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>参数

图表标记有两个参数：chart id 和 viewid。

**chart id**

图表的可视化效果 ID。 可通过导出图表获取此信息。

**viewid**

在视图编辑器中打开时的实体 ID。 

## <a name="powerbi"></a>powerbi

在页面内添加 Power BI 仪表板和报表。 可在网页中的**复制**字段内或 Web 模板中的**源**字段内添加此标记。 有关向门户中的网页添加 Power BI 报表或仪表板的步骤，请参阅[向门户中的网页添加 Power BI 报表或仪表板](../admin/add-powerbi-report.md)。

> [!NOTE]
> 要使该标记生效，必须从 Power Apps 门户管理中心[启用 Power BI 集成](../admin/set-up-power-bi-integration.md)。 如果未启用 Power BI 集成，则不显示仪表板或报表。

### <a name="parameters"></a>参数

powerbi 标记接受以下参数：

**path**

Power BI 报表或仪表板的路径。 如果 Power BI 报表或仪表板安全，则必须提供身份验证类型。

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Power BI 报表或仪表板所需身份验证的类型。 此参数的有效值为：

- **匿名**：允许您将发布嵌入到 Web Power BI 报表。 默认身份验证类型为“匿名”。 身份验证类型使用“匿名”时，必须按照以下说明获取 Power BI 报表 URL：[从 Power BI 发布到 Web](https://docs.microsoft.com/power-bi/service-publish-to-web)

- **AAD**：允许您将安全的 Power BI 报表或仪表板共享给经过身份验证的 Power BI Azure Active Directory 用户。

- **powerbiembedded**：允许您将安全的 Power BI 报表或仪表板共享给没有 Power BI 许可证或 Azure Active Directory 身份验证设置的外部用户。 有关 Power BI Embedded 服务设置的信息，请参阅[启用 Power BI Embedded 服务](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)。 

添加安全 Power BI 报表或仪表板时，请确保其与门户 Azure Active Directory 或 Power BI Embedded 服务共享。 

> [!NOTE]
> `authentication_type` 参数的值不区分大小写。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

也可以根据一个或多个值筛选报表。 下面是用于筛选报表的语法：

URL?filter=**Table**/**Field** eq '**value**'

例如，假设要将报表筛选为仅显示联系人 Bert Hair 的数据。 必须为 URL 追加以下内容：

?filter=Executives/Executive eq 'Bert Hair'

下面是完整代码：

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

有关筛选报表的详细信息：[使用 URL 中的查询字符串参数筛选报表](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> 匿名报表不支持筛选。 

也可以使用 `capture ` Liquid 变量创建动态路径，如下所示：

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

有关 Liquid 变量的详细信息：[变量标记](variable-tags.md)

**tileid**

显示仪表板的指定磁贴。 必须提供磁贴的 ID。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**角色**

分派给 Power BI 报表的角色。 仅当 **authentication_type** 参数设置为 **powerbiembedded** 时，此参数才有效。

如果已在 Power BI 中定义了角色并将其分派给报表，则必须在 **powerbi** Liquid 标记中指定相应角色。 可通过角色筛选报表中显示的数据。 可指定多个角色，并以逗号分隔。 有关在 Power BI 中定义角色的详细信息，请参阅[使用 Power BI 的行级安全性 (RLS)](https://docs.microsoft.com/power-bi/service-admin-rls)。

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

如果已经为 Power BI 分派了角色，但未在 Liquid 标记中指定 **roles** 参数，将显示错误。

> [!TIP]
> 如果要将门户中定义的 Web 角色用作 Power BI 角色，则可定义变量并为其分派 Web 角色。 然后可在该 Liquid 标记中使用定义的变量。
>
> 假设已在门户中将两个 Web 角色定义为 Region_East 和 Region_West。 可使用以下代码联接这两个角色：`{% assign webroles = user.roles | join: ", " %}`
>
> 在上面的代码段中，`webroles` 是一个变量，而 Region_East 和 Region_West Web 角色将存储在这个变量中。
>
> 按照下面的方法在 Liquid 标记中使用这个 `webroles` 变量：
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>可编辑

为具有该对象内容编辑权限的用户呈现特定 Power Apps 门户 CMS 对象，形式为可编辑对象。 可编辑对象包括[page](liquid-objects.md#page)、[snippets](liquid-objects.md#snippets) 和 [weblinks](liquid-objects.md#weblinks)。  

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

提供给 editable 的第一个参数是可编辑的对象。 例如，这可以是 Web 链接集、片段或当前页。 可选的第二个参数用于指定要呈现和编辑的对象中的属性名称或密钥。 例如，这可能是实体属性的名称或片段名称。

在这些初始参数之后，标记支持多个可选的已命名参数。

**class**

为此标记呈现的根元素指定 class 属性值。

**default**

可编辑项没有值时将呈现默认值。

**escape**

布尔值表示该标记呈现的值是否将使用 HTML 编码。 默认为 false。

**liquid**

布尔值表示是否处理该标记呈现的文本值中找到的所有 Liquid 模板代码。 默认为 true。

**tag**

此标记呈现的容器 HTML 标记的名称。 默认情况下，此标记将呈现 div 元素。 通常建议您选择 div 或 span 作为该参数的值。

**title**

在内容编辑界面中指定此可编辑项目的标签。 如果未提供任何内容，将自动生成友好标签。

**类型**

字符串值表示要为可编辑文本值显示的编辑界面类型。 对于此参数的有效值为 html 或 text。 默认值为 html。

## <a name="entitylist"></a>entitylist

按名称或 ID 加载特定实体列表。 实体列表的属性可以使用标记块中提供的 [entitylist 对象](liquid-objects.md#entitylist)进行访问。 若要呈现实体列表的实际结果记录，请在区块中使用 [entityview](#entityview) 标记。  

如果成功加载实体列表，则将呈现区块中的内容。 如果未找到实体列表，则将不会呈现区块内容。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
默认情况下，将为 entitylist 对象指定变量名称 entitylist。 或者，可以提供不同的变量名称。

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>参数

仅提供 id、name 或 key **之一**，以选择要加载的实体列表。

**id**

按 [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) ID 加载实体列表。 id 必须是可以解析为 GUID 的字符串。  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

通常，将不会使用文字 GUID 字符串。 而是，使用另一个变量的 GUID 属性来指定 id。

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

按名称加载实体列表。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

按 ID **或** 名称加载实体列表。 如果提供的关键值可解析为 [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier)，实体列表将按 ID 加载。 否则，将按名称加载。

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

加载用于选择实体列表本地化标签的 Power Apps 整数语言代码。 如果未提供 language\_code，将使用门户应用程序 Power Apps 连接的默认语言。

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

按名称或 ID 加载特定 Power Apps 视图。 视图的属性 视图列元数据、分页结果记录等可使用标记区块中提供的 [entityview 对象](liquid-objects.md#entityview)进行访问。  

如果成功加载视图，则将呈现区块中的内容。 如果未找到视图，则将不会呈现区块内容。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

默认情况下，将为 entityview 对象指定变量名称 entityview。 或者，可以提供不同的变量名称。

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

如果 entityview 嵌套在 entitylist 块中，它将继承实体列表中的默认配置（结果页面大小、筛选选项等）. 如果没有将视图 id 或 name 参数提供给 entityview，它将从包含的 entitylist 来加载默认视图。

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>参数

提供 id **或** logical\_name **之一**以及 name 来选择要加载的 Power Apps 视图。 如果两者均未提供，并且 entityview 标记嵌套在 entitylist 标记中，则将加载包含 entitylist 的默认视图。

**id**

id 必须是可以解析为 GUID 的字符串。

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

通常，将不会使用文字 GUID 字符串。 而是，使用另一个变量的 GUID 属性来指定 id。

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

要加载的视图的 Power Apps 实体逻辑名称。 必须与 name 结合使用。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

要加载的视图的 Power Apps 名称。 必须与 logical\_name 结合使用。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

指定是否按用户或帐户筛选视图结果。 必须具有字符串值“user”或“account”。

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

指定用于筛选视图结果的实体列表元数据筛选器表达式。 此参数仅在 entityview 与 entitylist 结合使用时有效。 大多数情况下，此参数设置基于 [request](liquid-objects.md#request)。  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

为视图结果排序指定排序表达式。 排序表达式可以包含一个或多个实体属性逻辑名称，后跟 ASC 或 DESC 的排序方向。

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

指定要加载的视图结果页面。 如果未指定此参数，则会加载结果的第一页。

必须向该参数传递整数值或可解析为整数的字符串。 如果已为此参数提供值，但该值为空或无法解析为整数，则将加载结果的第一页。

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

指定要为当前结果页面加载的结果数量。 如果未提供此参数的值，并在 [entitylist](#entitylist) 块中使用 entityview，则将使用实体列表页面大小。 如果不在 entitylist 块中，将使用默认值 10。

必须向该参数传递整数值或可解析为整数的字符串。 如果已为此参数提供值，但该值为空或无法解析为整数，则将加载结果的第一页。

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

指定用于筛选视图结果的搜索表达式。 简单的关键字搜索表达式将按照属性是否以关键字开始进行筛选。 通配符 \* 也可包含在表达式中。

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数，以便根据用户输入设置搜索筛选器。  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

指定是否对视图结果应用实体权限筛选。 默认情况下，此参数设置为 false。 如果在 entitylist 块中使用 entityview，则将从实体列表配置中继承此参数的值。

必须向该参数传[布尔](liquid-types.md#boolean)值或可解析为布尔值（true、false）的字符串。 如果已为此参数提供值，但该值为空或无法解析为布尔值，则默认将使用 false。  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

要加载的用于选择实体视图标签（列标签等）的 Power Apps 整数语言代码。 如果未提供 language\_code，将使用门户应用程序 Power Apps 连接的默认语言。

如果在 entitylist 块中使用 entityview，entityview 将从 entitylist 中继承其语言代码配置。

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

根据门户搜索索引执行查询。 匹配的结果可以使用标记块中提供的 [searchindex](liquid-objects.md#searchindex) 进行访问。  

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

默认情况下，将为搜索索引对象指定变量名称 searchindex。 或者，可以提供不同的变量名称。

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>参数

searchindex 标记接受以下参数。

**query**

用于匹配结果的查询。 此参数可用于接受用户指定的索引查询部分（如果有的话）。

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

此参数支持 [Lucene 查询分析程序语法](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)。

**filter**

用于匹配结果的其他查询。 如有必要，此参数可用于开发人员指定的结果筛选器。

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

此参数支持 [Lucene 查询分析程序语法](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)。  

> [!Note]     
> 筛选器和查询的不同点是，虽然两者都接受 Lucene 查询分析程序语法，但查询更能包容此语法的解析方式，ߝ因为按照预期，大多数最终用户将不会注意到此语法。 因此，如果根据此语法无法解析 query，则整个查询将转义并作为查询文本提交。 另一方面，query 将严格解析并在语法无效时返回错误。

**logical\_names**

限制匹配结果的 Power Apps 实体逻辑名称，形式为逗号分隔的字符串。 如果不提供，将返回所有匹配的实体。

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

将返回搜索结果页面。 如果不提供，将返回第一页 (1)。

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

常见使用案例是根据 [request](liquid-objects.md#request) 设置此参数。  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

将返回的结果页面的大小。 如果未提供，将使用默认大小 10。

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

按名称或 ID 完全呈现已配置 Power Apps 的实体窗体。  

> [!Note]
> entityform 标记仅可用于基于 <em>[Web 模板](store-content-web-templates.md)</em>的页面模板中呈现的内容。 尝试在基于重写的页面模板中使用标记将不会呈现任何内容。 每个页面仅可呈现一个 entityform 或 webform 标记。 不会呈现第一个标记之后的 entityform 或 webform 标记。       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>参数

**name**

希望加载的实体窗体的名称。

`{% entityform name:My Entity Form %}`

## <a name="webform"></a>webform

按名称或 ID 完全呈现已配置 Power Apps 的 Web 窗体。 webform 标记仅可用于基于 [Web 模板](store-content-web-templates.md)的页面模板中呈现的内容。 尝试在基于重写的页面模板中使用标记将不会呈现任何内容。 每个页面仅可呈现一个 entityform 或 webform 标记。 不会呈现第一个标记之后的 entityform 或 webform 标记。                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>参数

**name**

希望加载的 Web 窗体的名称。

`{% webform name:My Web Form %}`


### <a name="see-also"></a>另请参阅

[控制流标记](control-flow-tags.md)<br>
[迭代标记](iteration-tags.md)<br>
[变量标记](variable-tags.md)<br>
[模板标记](template-tags.md)
