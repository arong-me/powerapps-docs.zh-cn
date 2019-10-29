---
title: 为门户使用液体运算符 |MicrosoftDocs
description: 了解门户中可用的液体运算符。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976521"
---
# <a name="understand-liquid-operators"></a>了解 Liquid 运算符

液体有权访问所有常见逻辑 and 比较运算符。 它们可用于标记（如**if**和**除外**）。

## <a name="basic-operators"></a>基本运算符

| ==    | 对应                          |
|-------|---------------------------------|
| !=    | 不等于                  |
| &gt;  | 大于                    |
| &lt;  | 小于                       |
| &gt;= | 大于或等于        |
| &lt;= | 小于或等于           |
| 或    | 条件 A**或**条件 B  |
| 与   | 条件 A**和**条件 B |

## <a name="contains"></a>有

包含字符串中是否存在子字符串的测试。

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains 还可以测试字符串数组中是否存在字符串。

## <a name="startswith"></a>startswith

startswith 测试某个字符串是否以给定的子字符串开头。

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith 测试某个字符串是否以给定的子字符串结束。

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>另请参阅

[使用 web 模板存储源内容](store-content-web-templates.md)  
[液体类型](liquid-types.md)  
[增值税](liquid-conditional-operators.md)  
[液体对象](liquid-objects.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md) 