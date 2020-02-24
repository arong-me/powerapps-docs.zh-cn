---
title: 为门户使用 Liquid 标记 | MicrosoftDocs
description: 了解门户中的可用 liquid 标记。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3f85e4b86b305696f5b155c7e9e3b773f8ba2103
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981085"
---
# <a name="available-liquid-tags"></a>可用 Liquid 标记

用于告知模板要执行操作的程序逻辑的组成标记。 标记封装在 {% %} 中。

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>空格控件

通常，Liquid 会逐一呈现变量和标记块之外的所有内容，而空格保持原样。 有时，您不想要额外的空格，但仍然希望模板格式清晰（需要空格）。

您可以告诉引擎通过向开始或结束区块标记添加连字符 (-) 来去除所有前导和结尾空格。

**代码**

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

[Liquid 类型](liquid-types.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 筛选器](liquid-filters.md) 
