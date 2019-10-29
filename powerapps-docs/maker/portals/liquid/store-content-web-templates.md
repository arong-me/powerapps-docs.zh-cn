---
title: 使用 web 模板在门户中存储源内容 |MicrosoftDocs
description: 使用 web 模板在门户中存储内容的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2abdf23376cfbcc0b591afe2efb1699144fbef8f
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974520"
---
# <a name="store-source-content-by-using-web-templates"></a>使用 web 模板存储源内容

Web 模板是 powerapps 门户中包含的 PowerApps 实体（adx\_webtemplate），用于存储模板源内容。 Web 模板通常包含液体用于动态内容呈现，是用于将液体模板与 PowerApps 门户系统的其余部分进行集成的中心实体。

Web 模板可以包含在其他内容中，也可以与其他模板结合使用模板标记，并通过其**名称**属性在这些标记中引用。 它们还可用于创建整个自定义页面模板，或为门户网站创建自定义页眉和页脚。

## <a name="web-template-attributes"></a>Web 模板属性

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   名称    |                                                                         模板的名称。 用于引用此模板（如果它包含在其他内容中）或由其他模板扩展。                                                                         |
|  源程序   |                                  模板的源内容。 在 PowerApps 中，将为此字段提供语法突出显示和其他代码编辑功能的源代码编辑器。                                  |
| MIME 类型 | （可选）为模板内容提供 MIME 类型。 如果未提供任何内容，则采用文本/html 类型。 此值仅用于模板与页面模板关联的情况，并控制该模板的所有内容的呈现。 |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Web 模板作为页面模板

Web 模板可以与页面模板结合使用，为 PowerApps 门户内容管理系统创建新模板。 这可以完全在 PowerApps 内完成，无需编写 .NET 代码或重新部署门户应用程序。

若要基于 web 模板创建新的页面模板，请在创建新页面模板记录时选择一**种**web 模板。 然后选择 " **Web" 模板**。

请注意，选项**使用网站页眉和页脚**（默认选中）。 如果选中此复选控件，你的 Web 模板将控制在全局网站页眉和页脚之间呈现所有页面内容。 如果未选中此选项，则在呈现 HTML 时，Web 模板将负责呈现整个响应，这意味着从 doctype 到根 &lt;HTML&gt; 标记，以及两者之间的所有内容。

尽管 Web 模板最常见的用例是呈现 HTML，但通过取消选中 "**使用网站标头和页脚**" 来呈现整个响应（通过取消选择 "使用网站" 页眉和页脚），可以选择呈现所选的任何基于文本的格式。 这是 Web 模板的**MIME 类型**属性的相关位置。 如果呈现的页面模板不使用网站页眉和页脚，则会将 HTTP 响应 Content-type 标头设置为关联 Web 模板的 MIME 类型。 （如果未提供 MIME 类型，则将使用文本/html。）这为您提供了各种用于使用液体呈现非 HTML 内容的选项。 常见的用例是通过设置应用程序/RSS + xml 的 MIME 类型来呈现[RSS](http://en.wikipedia.org/wiki/RSS)源。  

## <a name="web-templates-as-website-headers-and-footers"></a>Web 模板作为网站页眉和页脚

Web 模板还可以用于替代 PowerApps 门户使用的全局页眉和页脚。 为此，请将网站的 "**标题模板**" 或 "**表尾模板**" 字段设置为所选的 web 模板。 请注意，如果你覆盖**网站标题**，则所选模板会为你的站点接口元素（通常由默认操作处理）的导航、登录/注销链接、搜索界面等呈现责任。标题模板。

## <a name="built-in-web-templates"></a>内置 web 模板

PowerApps 门户中有一组预制的液体模板可用。 若要使用它们，必须按名称包含它们，并使用下面的列表作为参考。

| 名称                        | 描述                                                                                                                                                                                                                             | 代码                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 广告                          | 此模板按名称呈现广告，或从广告位置呈现随机广告。                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| 博客                       | 此模板呈现列表组中的最新博客文章。                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| 痕迹导航                 | 此模板将上级页面的链接从当前页面呈现回主页。                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| 子链接列表组       | 此模板呈现指向列表组中当前页面的任何子页面的链接。                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| 事件：即将推出            | 此模板可呈现从现在到60天之间发生的事件的链接。                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| 论坛                      | 此模板呈现网站的论坛列表，其中包含各自的线程和帖子数。                                                                                                                                 | `{% include 'forums' %}`                                       |
| 布局1列             | 此模板呈现单列布局，其中包含痕迹导航、页面标题和页面复制内容。                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| 布局2列宽左   | 此模板呈现两个列布局。 左侧的列大于右侧的宽度。 它在页面顶部包含痕迹导航页面标题，页面复制内容位于左列。                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| 布局2列级右侧  | 此模板呈现两个列布局。 右侧列的宽度大于左侧。 它在页面顶部包含痕迹导航页面标题，页面复制内容位于右栏。                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| 布局3列宽中部 | 此模板呈现三列布局。 中间列的宽度大于左侧和右侧。 布局包含痕迹导航，页面顶部有页面标题，页面复制内容位于中间栏中。   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| 页面复制                   | 此模板可呈现支持嵌入液体的可编辑页面副本内容 HTML。                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| 页眉                 | 此模板呈现页面标题。                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| 检测                        | 此模板按名称或从轮询位置进行随机轮询来呈现轮询。                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Search                      | 此模板使用单个文本输入和搜索按钮呈现基本搜索窗体。                                                                                                                                                   | `{% include 'search' %}`                                                             |
| 侧面导航             | 此模板呈现垂直树视图样式导航。 它具有指向上级页面的链接，这些页面返回到第一个级别（或指定的深度偏移）、指向当前页面的同级页面的链接，以及指向当前页面的子页面的链接。 | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| 片段                     | 此模板按名称呈现可编辑的 HTML 内容片段。                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| 顶部导航栏              | 此模板使用主导航 web 链接集的下拉菜单呈现可编辑的导航栏。                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Weblink 列表组          | 此模板为 web 链接集呈现列表链接组。                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>另请参阅

[了解液体运算符](liquid-operators.md)  
[液体类型](liquid-types.md)  
[增值税](liquid-conditional-operators.md)  
[液体对象](liquid-objects.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md)  
