---
title: 为门户使用液体条件运算符 |MicrosoftDocs
description: 了解门户中可用的液体条件运算符。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975003"
---
# <a name="available-liquid-conditional-operators"></a>可用 Liquid 条件运算符

在条件语句中使用时（**如果**不**是），** 某些液体值将视为 true，某些液体值将被视为 false。

在液体，空值和布尔值 false 被视为 false; 其他所有内容都被视为 true。 空字符串、空数组等将被视为 true。 有关示例，

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
如果需要，可以使用特殊值测试空字符串和数组。

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
你还可以使用特殊大小属性测试[液体类型](liquid-types.md)、[液体类型](liquid-types.md)或[液体类型](liquid-types.md)的大小。

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

|                           | True | false |
|---------------------------|------|-------|
| True                      | *    |       |
| false                     |      | *     |
| 无效                      |      | *     |
| String                    | *    |       |
| 空字符串              | *    |       |
| 0                         | *    |       |
| 1，3.14                   | *    |       |
| 数组或字典       | *    |       |
| 空数组或字典 | *    |       |
| 对象                    | *    |       |

### <a name="see-also"></a>另请参阅

[使用 web 模板存储源内容](store-content-web-templates.md)  
[了解液体运算符](liquid-operators.md)  
[液体类型](liquid-types.md)  
[液体对象](liquid-objects.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md)  
