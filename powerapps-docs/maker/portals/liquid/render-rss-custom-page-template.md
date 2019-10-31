---
title: 为门户使用自定义页面模板呈现 RSS 源 | MicrosoftDocs
description: 有关如何创建自定义页面模板并用于呈现 RSS 源的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>创建用于呈现 RSS 源的自定义页面模板
在此示例中，我们将创建一个自定义页面模板，用于呈现新闻文章的 [RSS 源](http://en.wikipedia.org/wiki/RSS)，使用 Liquid 和 Web 模板页模板。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [使用 Web 模板存储源内容](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>步骤 1：创建新 PowerApps 视图

首先，我们将创建我们将用于加载源数据的新 PowerApps 视图。 在此示例中，我们将在网页中建立一个视图，然后使用此实体存储我们的文章。 我们可以使用此视图排序和筛选结果，并作为列包含我们需要在 Liquid 模板中提供的实体属性。

![编辑页面模板](../media/edit-page-template.png "编辑页面模板")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>步骤 2：创建 RSS 源的 Web 模板

在此步骤中，我们将为 RSS 源创建 Web 模板。 此模板要应用于我们网站的特定网页，因此我们将使用该页的标题和摘要作为源的标题和说明。 我们将使用 entityview 标记加载我们新创建的“新闻文章”视图。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [PowerApps Common Data Service 实体标记](portals-entity-tags.md). 请注意，我们还将 Web 模板的 **MIME 类型**字段设置为 application/rss+xml。 这指示在呈现我们的模板时可以是哪种响应内容类型。  

![为 RSS 源配置 Web 模板](../media/web-template-rss-feed.png "为 RSS 源配置 Web 模板")  

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

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>步骤 3：创建用于分派 RSS 源模板的页面模板

现在，我们将创建新页面模板，允许我们将 RSS 源模板分配到网站中的任何网页。 请注意，我们取消选择**使用网站标题和脚注**，因为我们希望接管我们的源的整个页面响应的呈现。

![为 RSS 源配置页面模板](../media/page-template-rss-feed.png "为 RSS 源配置页面模板")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>步骤 4：创建承载 RSS 源的网页

x现在只需使用 RSS 源模板创建新网页来托管我们的源。 在我们请求此新网页时，我们将收到我们的 RSS 源 XML：

![RSS 源示例](../media/rss-feed-example.png "RSS 源示例")  

在此示例中，我们看到了我们如何合并 Liquid、Web 模板、PowerApps 视图和门户内容管理功能来创建自定义 RSS 源。 这些功能的组合为任何门户应用程序增加强大的自定义功能。

### <a name="see-also"></a>另请参阅

[使用 Liquid 和 Web 模板页面模板创建自定义页面模板](create-custom-template.md)  
[呈现与当前页关联的实体列表](render-entity-list-current-page.md)  
[呈现网站标题和主要导航栏](render-site-header-primary-navigation.md)  
[使用混合导航最多呈现页面层次结构的三个级别](hybrid-navigation-render-page-hierachy.md)  

