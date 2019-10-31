---
title: 为门户使用变量标记 | MicrosoftDocs
description: 了解门户中的可用变量标记
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="variable-tags"></a>变量标记

变量标记用于创建新 Liquid 变量。

## <a name="assign"></a>分派

创建新变量。 分派也可以使用[筛选器](liquid-filters.md)修改值。  

**代码**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**输出**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>捕获

在其块中捕获内容并将其分派给变量。 此内容然后可以在以后使用输出标记呈现。

**代码**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**输出**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>另请参阅

[控制流标记](control-flow-tags.md)<br>
[迭代标记](iteration-tags.md)<br>
[模板标记](template-tags.md)<br>
[PowerApps Common Data Service 实体标记](portals-entity-tags.md)
