---
title: 为门户使用控制流标记 | MicrosoftDocs
description: 了解门户中的可用控制流标记。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 1cdc608253bef652445f0eb689435f0089629979
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977257"
---
# <a name="control-flow-tags"></a>控制流标记

控制流标记确定应执行哪个代码块，以及基于特定条件应呈现哪些内容ߝ。 条件使用可用的 [Liquid 运算符](liquid-operators.md)构建，或只是基于[给定值的真或假](liquid-conditional-operators.md)。  

## <a name="if"></a>if

如果指定条件匹配，执行代码块。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

与 if 相似，如果**不**满足指定条件，则不执行代码块。

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

添加更多条件到 if 或 unless 块。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

将变量与不同值进行比较以及执行每个值的不同代码块的开关语句。

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>另请参阅

[迭代标记](iteration-tags.md)<br>
[变量标记](variable-tags.md)<br>
[模板标记](template-tags.md)<br>
[Power Apps Common Data Service 实体标记](portals-entity-tags.md)
