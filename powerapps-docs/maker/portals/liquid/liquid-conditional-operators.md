---
title: 为门户使用 Liquid 条件运算符 | MicrosoftDocs
description: 了解门户中的可用 liquid 条件运算符。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-conditional-operators"></a>可用 Liquid 条件运算符

在条件语句（**if**、**unless**）中使用时，有些 Liquid 值将视为 true，有些则视为 false。

在 Liquid 中，null 和布尔值 false 被视为 false，其他所有项均视为 true。 空字符串、空数组等被视为 true。 例如，

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
如果需要，您可以使用特殊值 empty 对空字符串和数组进行测试。

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
也可以使用特殊的大小属性测试 [Liquid 类型](liquid-types.md)、[Liquid 类型](liquid-types.md)或 [Liquid 类型](liquid-types.md)的大小。

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>摘要

|                           | 真 | 假 |
|---------------------------|------|-------|
| 真                      | ×    |       |
| 假                     |      | ×     |
| Null                      |      | ×     |
| 字符串                    | ×    |       |
| 空字符串              | ×    |       |
| 0                         | ×    |       |
| 1, 3.14                   | ×    |       |
| 数组或词典       | ×    |       |
| 空数组或词典 | ×    |       |
| 对象                    | ×    |       |

### <a name="see-also"></a>另请参阅

[使用 Web 模板存储源内容](store-content-web-templates.md)  
[了解 Liquid 运算符](liquid-operators.md)  
[Liquid 类型](liquid-types.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md)  
