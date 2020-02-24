---
title: 为门户使用变量标记 | MicrosoftDocs
description: 了解门户中的可用变量标记
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f9a56a9bccc8445dc7540f6ade402d5988ec1ffc
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978797"
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
[Power Apps Common Data Service 实体标记](portals-entity-tags.md)
