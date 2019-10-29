---
title: 使用 "液体" 和 "web 模板" 页面模板为门户创建自定义页面模板 |MicrosoftDocs
description: 使用液体运算符创建自定义页面模板的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7717bd75fe7149ea3b0af957055975ad10e752ae
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975049"
---
# <a name="create-a-custom-page-template"></a>创建自定义页面模板

在此示例中，我们将使用液体和基于 web 模板的页面模板来创建自定义页面模板。 [使用 web 模板 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] 存储源内容](store-content-web-templates.md)。 我们的目标是构建一个简单的两列模板，该模板[将 web 链接设置](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links)为左侧导航，页面内容在右侧。 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>步骤1：创建 web 模板并编写液体模板代码

首先，我们将创建 Web 模板并编写液体模板代码。 我们很可能会在将来的模板中重复使用此模板的一些公共元素。 接下来，我们将创建一个通用的基本模板，该模板将使用特定的模板进行扩展。 我们的基本模板将提供痕迹链接和页面标题/标题，并定义单列布局：

> [!div class=mx-imgBorder]
![Web 模板 one 单列布局](../media/web-template-two-column-layout.png "Web 模板一列布局")

> [!TIP]
> 阅读有关使用块和扩展标记的模板继承：[模板标记](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>两列布局（Web 模板）

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>步骤2：创建新的 web 模板以扩展我们的基本布局模板

使用与当前页面关联的导航 web 链接集导航链接来创建新的 web 模板，该模板可扩展我们的基本布局模板。

> [!div class=mx-imgBorder]
![Web 模板 web 链接左侧导航布局](../media/web-template-weblinks-left-navigation-layout.png "web 模板 web 链接左侧导航布局")  

> [!TIP]
> 熟悉如何使用[weblinks](liquid-objects.md#weblinks)对象加载 web 链接集。

### <a name="weblinks-left-navigation-web-template"></a>Weblinks 左导航（Web 模板）

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>步骤3：基于 web 模板创建新的页面模板

在此步骤中，我们将创建一个新的页面模板，该模板基于我们在上一步中创建的 web 模板。

> [!div class=mx-imgBorder]
![页面模板 weblinks 左侧导航布局](../media/page-template-weblinks-left-navigation-layout.png "页模板 weblinks 左导航布局")  

## <a name="step-4-create-a-web-page-to-display-content"></a>步骤4：创建显示内容的网页

现在，剩下的工作就是创建一个使用页面模板的网页，并具有关联的 Web 链接集，并获得结果。

> [!div class=mx-imgBorder]
具有(../media/web-page-left-navigation.png "左侧")导航的![左侧导航]网页网页  

### <a name="see-also"></a>另请参阅

[创建用于呈现 RSS 源的自定义页面模板](render-rss-custom-page-template.md)  
[呈现与当前页关联的实体列表](render-entity-list-current-page.md)  
[呈现网站页眉和主导航栏](render-site-header-primary-navigation.md)  
[使用混合导航最多呈现三个级别的页层次结构](hybrid-navigation-render-page-hierachy.md)  

