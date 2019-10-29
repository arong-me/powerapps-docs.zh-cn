---
title: 为门户使用液体标记 |MicrosoftDocs
description: 了解门户中可用的液体标记。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976544"
---
# <a name="available-liquid-tags"></a>可用 Liquid 标记

标记构成编程逻辑，该逻辑告知模板要执行的操作。 标记已包装在 {%%} 中。

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>空格控件

通常，液体按原义显示变量和标记块以外的所有内容。 偶尔，你不需要额外的空白区域，但仍需要完全设置模板的格式，这需要空格。

通过向开始或结束块标记添加连字符（-），可以告知引擎去掉所有前导或尾随空格。

**编写**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**输出**

```
12345
```
### <a name="see-also"></a>另请参阅

[液体类型](liquid-types.md)  
[液体对象](liquid-objects.md)  
[液体过滤器](liquid-filters.md) 
