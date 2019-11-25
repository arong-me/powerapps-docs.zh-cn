---
title: 使用 Web 模板存储门户的源内容 | MicrosoftDocs
description: 有关如何在门户中使用 Web 模板存储内容的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 76c8e525c5d5b612e055da9c43e14df55cec6e4f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757080"
---
# <a name="store-source-content-by-using-web-templates"></a>使用 Web 模板存储源内容

Web 模板是 PowerApps 门户随附的 PowerApps 实体 (adx\_webtemplate)，用于存储模板源内容。 Web 模板通常将包含动态内容呈现的 Liquid，是用于集成 Liquid 模板与 PowerApps 门户系统的其他部分的中心实体。

Web 模板可以包括在其他内容中或与使用模板标记的其他模板组合，并在这些标记中由标记的**名称**属性引用。 他们还可用来创建整个自定义页面模板，或者创建您的门户网站的自定义标题和脚注。

## <a name="web-template-attributes"></a>Web 模板属性

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   客户    |                                                                         模板的名称。 在此模板包括在其他内容中或由其他模板扩展时用于引用此模板。                                                                         |
|  来源   |                                  模板的源内容。 在 PowerApps 中，使用语法突出显示和其他代码编辑功能的源代码编辑器为此字段提供。                                  |
| MIME 类型 | 或者为模板内容提供 MIME 类型。 如果未提供任何内容，假设为 text/html 类型。 此值仅在模板与页面模版关联以及控制该模板所有内容的呈现时使用。 |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Web 模板用作页面模板

Web 模板可以与页面模板结合用于创建 PowerApps 门户内容管理系统的新模板。 这可以在 PowerApps 中完全执行，而无需编写 .NET 代码或重新部署您的门户应用程序。

当创建新网页模版记录时，若要创建基于 Web 模板的新页面模板，请选择一种**类型**的 Web 模板 。 然后选择 **Web 模板**。

请注意选项**使用网站标题和脚注**（默认选中）。 如果选中此项，Web 模板将控制全局网站标题和脚注之间所有页面内容的呈现。 如果此选项未选中，则 Web 模板将负责呈现您在呈现 HTML 时的整个响应，这意味着从 Doctype 到根 &lt;html&gt; 标记以及二者之间的所有内容。

当 Web 模板的最常用案例将会呈现 HTML 时，呈现整个响应（通过取消选择**使用网站标题和脚注**）提供给您呈现选择的任何基于文本的格式的选项。 这是 Web 模板的 **MIME 类型**属性变为相关的位置。 在不使用网站标题和脚注的页面模版呈现时，HTTP 响应 Content-Type 标题将设置为关联的 Web 模板的 MIME 类型。 （如果不提供 MIME Type，将使用text/html。）这样就可以通过各种选项使用 Liquid 呈现非 HTML 内容。 常用案例将呈现 [RSS](https://en.wikipedia.org/wiki/RSS) 源，方法是设置 MIME 类型 application/rss+xml。  

## <a name="web-templates-as-website-headers-and-footers"></a>作为网站标题和脚注的 Web 模板

Web 模板还可以用于替代 PowerApps 门户使用的全局标题和脚注。 为此，设置您的网站**标题模板**或**脚注模板**字段为您选择的 Web 模板。 请注意，如果您替代**网站标题**，您选择的模板将假设负责呈现正常由默认标题模板处理的网站界面元素的主要导航、登录/注销链接、搜索界面等。

## <a name="built-in-web-templates"></a>内置 Web 模板

PowerApps 门户中提供一套预创建的 Liquid 模板。 若要使用，必须按名称包含它们，并将下面的列表用作参考。

| 名称                        | 说明                                                                                                                                                                                                                             | 代码                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 广告                          | 该模板按名称呈现广告或广告位置的随机广告。                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| 博客                       | 此模板呈现列表组中的近期博客文章。                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| 导航痕迹                 | 该模板呈现上级页面从当前页返回主页的链接。                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| 子链接列表组       | 此模板呈现指向列表组中当前页的所有子页的链接。                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| 活动：即将推出            | 此模板呈现现在到从现在起 60 天之内发生的活动的链接。                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| 论坛                      | 此模板呈现网站论坛的列表及其各自的线程和帖子数量。                                                                                                                                 | `{% include 'forums' %}`                                       |
| 布局 1 列             | 此模板呈现包含导航痕迹、页面标题和页面副本内容的单个列布局。                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| 布局 2 列宽（左）   | 此模板呈现两列布局。 左侧的列宽于右侧列。 它包含导航痕迹、页面顶部的页面标题和位于左侧列的页面副本内容。                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| 布局 2 列宽（右）  | 此模板呈现两列布局。 右侧的列宽于左侧列。 它包含导航痕迹、页面顶部的页面标题和位于右侧列的页面副本内容。                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| 布局 3 列宽（中间） | 此模板呈现三列布局。 中间列宽于左侧和右侧列。 此布局包含导航痕迹和页面顶部的页面标题，以及位于中间列的页面副本内容。   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| 页面副本                   | 此模板呈现可编辑的页面副本内容 HTML，具有嵌入 Liquid 支持。                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| 页面标题                 | 此模板呈现页面标题。                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| 轮询                        | 该模板按名称呈现投票或投票位置的随机投票。                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| 搜索                      | 此模板呈现具有单一文本输入和搜索按钮的基本搜索窗体。                                                                                                                                                   | `{% include 'search' %}`                                                             |
| 侧栏导航             | 此模板呈现垂直树视图样式的导航。 它包含指向返回第一级（或指定深度偏差）的上级页的链接，指向当前页同级页的链接和指向当前页子页的链接。 | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| 片段                     | 该模板按名称呈现可编辑的 HTML 内容片段。                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| 顶部导航              | 该模板呈现可编辑的导航栏，包含用于主导航网站链接设置的下拉菜单。                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Web 链接列表组          | 此模板显示 Web 链接集的链接列表组。                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>另请参阅

[了解 Liquid 运算符](liquid-operators.md)  
[Liquid 类型](liquid-types.md)  
[条件](liquid-conditional-operators.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md)  
