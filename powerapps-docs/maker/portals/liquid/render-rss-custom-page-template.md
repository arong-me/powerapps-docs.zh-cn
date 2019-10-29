---
title: 使用门户的自定义页模板呈现 RSS 源 |MicrosoftDocs
description: 有关创建自定义页面模板并将其用于呈现 RSS 源的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 9ad14cb5e3385f559ded6e3ac18b0455f93178d5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974750"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>创建用于呈现 RSS 源的自定义页面模板
在此示例中，我们将创建一个自定义页面模板，用于呈现使用液体和 Web 模板页面模板的新闻文章的[RSS 源](http://en.wikipedia.org/wiki/RSS)。 [使用 web 模板 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] 存储源内容](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>步骤1：创建新的 PowerApps 视图

首先，我们将创建一个新的 PowerApps 视图，我们将使用这些视图为源加载数据。 在此示例中，我们将使其成为网页上的一个视图，并使用此实体来存储我们的文章。 可以使用此视图配置结果的排序和筛选，并将其作为列包含在液体模板中提供的实体属性。

![编辑页面模板](../media/edit-page-template.png "编辑页面模板")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>步骤2：创建用于 RSS 源的 web 模板

在此步骤中，我们将为 RSS 源创建一个 web 模板。 此模板将应用于网站中的特定网页，因此，我们将使用该页面的标题和摘要作为源的标题和说明。 我们将使用 entityview 标记来加载新创建的新闻文章视图。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [PowerApps common data service 实体标记](portals-entity-tags.md)。 请注意，我们还将 Web 模板的 " **MIME 类型**" 字段设置为 "应用程序/rss + xml"。 这指示呈现模板时的响应内容类型。  

![为 rss 源配置 web 模板]为(../media/web-template-rss-feed.png "rss 源配置 web 模板")  

### <a name="rss-feed-web-template"></a>RSS 源（Web 模板）

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>步骤3：创建用于分配 RSS 源模板的页面模板

现在，我们将创建一个新的页面模板，使我们能够将 RSS 源模板分配到网站中的任何网页。 请注意，我们取消选择**使用网站页眉和页脚**，因为我们想要对我们的源进行整个页面响应的呈现。

![为 rss 源配置页面模板]为(../media/page-template-rss-feed.png "rss 源配置页面模板")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>步骤4：创建用于托管 RSS 源的网页

现在，剩下的就是使用 RSS 源模板来创建一个新的网页来托管我们的源。 当我们请求这个新的网页时，我们将收到 RSS 源 XML：

(../media/rss-feed-example.png "Rss 源") ![rss 源示例的示例]  

在此示例中，我们已了解如何合并液体、Web 模板、PowerApps 视图和门户内容管理功能，以创建自定义 RSS 源。 这些功能的组合为任何门户应用程序添加了功能强大的自定义功能。

### <a name="see-also"></a>另请参阅

[使用液体和 web 模板页模板创建自定义页面模板](create-custom-template.md)  
[呈现与当前页关联的实体列表](render-entity-list-current-page.md)  
[呈现网站页眉和主导航栏](render-site-header-primary-navigation.md)  
[使用混合导航最多呈现三个级别的页层次结构](hybrid-navigation-render-page-hierachy.md)  

