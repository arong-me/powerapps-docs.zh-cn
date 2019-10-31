---
title: 为门户使用 Liquid 运算符 | MicrosoftDocs
description: 了解门户中的可用 liquid 运算符。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="understand-liquid-operators"></a>了解 Liquid 运算符

Liquid 可以访问所有公共逻辑和比较运算符。 这些可用于标记中，例如，**如果**和**除非**。

## <a name="basic-operators"></a>基本运算符

| ==    | 等于                          |
|-------|---------------------------------|
| !=    | 不等于                  |
| &gt;  | 大于                    |
| &lt;  | 小于                       |
| &gt;= | 大于或等于        |
| &lt;= | 小于或等于           |
| 或    | 条件 A **或**条件 B  |
| 和   | 条件 A **和**条件 B |

## <a name="contains"></a>包含

contains 用于测试字符串中的子字符串显示。

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains 也可测试字符串阵列内的字符串显示。

## <a name="startswith"></a>startswith

startswith 用于测试字符串是否以特定子字符串开头。

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith 用于测试字符串是否以特定子字符串结尾。

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>另请参阅

[使用 Web 模板存储源内容](store-content-web-templates.md)  
[Liquid 类型](liquid-types.md)  
[条件](liquid-conditional-operators.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md) 