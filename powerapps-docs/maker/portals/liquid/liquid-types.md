---
title: 为门户使用 Liquid 类型 | MicrosoftDocs
description: 了解门户中的可用 liquid 类型。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e84ec3363f492231c218e0bb9f6e8a8d8b45fce6
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125033"
---
# <a name="available-liquid-types"></a>可用 Liquid 类型

Liquid 对象可以返回七个基本类型之一：**字符串**、**数字**、**布尔值**、**数组**、**词典**、**DateTime** 或**空**。 可以通过使用**分派**或**捕获**标记初始化 Liquid。

## <a name="string"></a>字符串

字符串通过在单括号或双括号中换行文本来声明。

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

获取具有 size 属性的字符串中的字符数。

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>号码

数字可以整数或浮动。

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

布尔值是 true 或 false。

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>Array

数组保留任何类型的值的列表。 可以通过使用 \[ \] 通过（零基）索引访问指定项目，使用**用于标记**迭代它们，使用 size 属性获取数组中项目的数量。

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>词典

词典保留可以由字符串键访问值的集合。 可以通过使用 \[ \] 由字符串键访问指定项目，使用**用于标记**迭代它们，使用 size 属性获取词典中项目的数量。

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>日期时间

DateTime 对象表示特定日期和时间。

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

空表示空的或不存在的值。 任何尝试返回空值的输出不会呈现任何内容。 它在条件中将会被视为 false。

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>另请参阅

[使用 Web 模板存储源内容](store-content-web-templates.md)  
[了解 Liquid 运算符](liquid-operators.md)  
[条件](liquid-conditional-operators.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md)  