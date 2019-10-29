---
title: 为门户使用变量标记 |MicrosoftDocs
description: 了解门户中可用的变量标记
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974405"
---
# <a name="variable-tags"></a>变量标记

可变标记用于创建新液体变量。

## <a name="assign"></a>将

创建新变量。 分配还可以使用[筛选器](liquid-filters.md)来修改值。  

**编写**

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

## <a name="capture"></a>抓住

捕获其块中的内容，并将其分配给变量。 稍后可以使用输出标记呈现此内容。

**编写**

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
[PowerApps common data service 实体标记](portals-entity-tags.md)
