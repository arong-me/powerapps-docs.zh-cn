---
title: 为门户使用 Liquid 标记 | MicrosoftDocs
description: 了解门户中的可用 liquid 标记。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708119"
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
