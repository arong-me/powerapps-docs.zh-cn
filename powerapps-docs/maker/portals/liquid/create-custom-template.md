---
title: 使用 Liquid 和 Web 模板页面模板为门户创建自定义页面模板| MicrosoftDocs
description: 有关如何使用 Liquid 运算符创建自定义页模板的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8fe2d6f6496c609a9811ddb4ca28c3df47d8e04d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757388"
---
# <a name="create-a-custom-page-template"></a>创建自定义页面模板

在此示例中，我们将使用 Liquid 和基于 Web 模板的页面模板创建自定义页面模板。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [使用 Web 模板存储源内容](store-content-web-templates.md)。 我们的目标是构建简单的两列式模板，该模板使用 [Web 链接集](../configure/manage-web-links.md)作为左侧导航，并在右侧显示页面内容。 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>步骤 1：创建 Web 模板并编写 Liquid 模板代码

首先，我们将创建 Web 模板并编写 Liquid 模板代码。 我们可能在将来的模板中重用此模板的部分通用元素。 因此，我们将创建可以使用我们的特定模板进行扩展的通用基本模板。 我们的基本模板将提供痕迹链接和我们的页面标题，并定义一列式布局：

> [!div class=mx-imgBorder]
![Web 模板一列布局](../media/web-template-two-column-layout.png "Web 模板一列布局")

> [!TIP]
> 使用块和扩展标记了解模板的继承：[模板标记](template-tags.md#extends)

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>步骤 2：创建用于扩展基本布局模板的新 Web 模板

使用与导航链接当前页面关联的导航 Web 链接集来创建用于扩展我们的基本布局模板的新 Web 模板。

> [!div class=mx-imgBorder]
![Web 模板 Web 链接左侧导航布局](../media/web-template-weblinks-left-navigation-layout.png "Web 模板 Web 链接左侧导航布局")  

> [!TIP]
> 了解如何使用 [weblinks](liquid-objects.md#weblinks) 对象加载 Web 链接集。

### <a name="weblinks-left-navigation-web-template"></a>Weblinks 左侧导航（Web 模板）

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>步骤 3：基于 Web 模板创建新的页面模板

在此步骤中，我们将创建基于之前步骤中创建的 Web 模板的新页面模板。

> [!div class=mx-imgBorder]
![页面模板 Web 链接左侧导航布局](../media/page-template-weblinks-left-navigation-layout.png "页面模板 Web 链接左侧导航布局")  

## <a name="step-4-create-a-web-page-to-display-content"></a>步骤 4：创建显示内容的网页

现在，剩下的任务是创建一个网页，该网页使用我们的页面模板并具有关联的 Web 链接集，我们将看到我们的结果。

> [!div class=mx-imgBorder]
![带左侧导航的网页](../media/web-page-left-navigation.png "带左侧导航的网页")  

### <a name="see-also"></a>另请参阅

[创建用于呈现 RSS 源的自定义页面模板](render-rss-custom-page-template.md)  
[呈现与当前页关联的实体列表](render-entity-list-current-page.md)  
[呈现网站标题和主要导航栏](render-site-header-primary-navigation.md)  
[使用混合导航最多呈现页面层次结构的三个级别](hybrid-navigation-render-page-hierachy.md)  

