---
title: 为门户使用 Liquid 条件运算符 | MicrosoftDocs
description: 了解门户中的可用 liquid 条件运算符。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 034c6741ac5555448f85fc08579855d6980490e2
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978313"
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
