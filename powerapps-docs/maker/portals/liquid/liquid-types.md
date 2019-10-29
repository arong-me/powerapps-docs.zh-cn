---
title: 使用液体类型作为门户 |MicrosoftDocs
description: 了解门户中可用的液体类型。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974934"
---
# <a name="available-liquid-types"></a>可用 Liquid 类型

液体对象可以返回七种基本类型之一：**字符串**、**数字**、**布尔值**、**数组**、**字典**、**日期时间**或**Null**。 可以使用**assign**或**capture**标记初始化液体变量。

## <a name="string"></a>String

字符串是通过在单引号或双引号中环绕文本来声明的。

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

获取具有 size 属性的字符串中的字符数。

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Number

数字可以是整数或浮点数。

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

布尔值为 true 或 false。

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>组成

数组包含任何类型的值的列表。 您可以使用 \[ \]通过（从零开始）索引访问给定项，使用**for 标记**对其进行循环访问，并使用 size 属性获取数组中的项数。

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>字典

字典保存可通过字符串键访问的值的集合。 您可以使用 \[ \]按字符串键访问给定项，使用**for 标记**循环访问该项，并使用 size 属性获取字典中的项数。

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>日期/时间

DateTime 对象表示特定日期和时间。

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>无效

Null 表示空值或不存在的值。 任何尝试返回 null 值的输出将不会呈现任何内容。 在条件中，它将被视为 false。

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>另请参阅

[使用 web 模板存储源内容](store-content-web-templates.md)  
[了解液体运算符](liquid-operators.md)  
[增值税](liquid-conditional-operators.md)  
[液体对象](liquid-objects.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md)  