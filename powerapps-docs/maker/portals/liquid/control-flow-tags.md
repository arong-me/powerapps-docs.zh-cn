---
title: 使用门户的控制流标记 |MicrosoftDocs
description: 了解门户中可用的控制流标记。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975095"
---
# <a name="control-flow-tags"></a>控制流标记

控制流标记确定应该执行的代码块以及应根据给定条件呈现的内容。 条件是使用可用的[液体运算符](liquid-operators.md)生成的，或者只是基于[给定值的真假或 falsehood 生成的](liquid-conditional-operators.md)。  

## <a name="if"></a>如果

如果满足给定条件，则执行代码块。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>直到

例如，在**不**满足给定条件的情况下，它将执行代码块。

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

向 if 或 if 块添加更多条件。

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

用于将变量与不同值进行比较的 switch 语句，并为每个值执行不同的代码块。

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
[PowerApps common data service 实体标记](portals-entity-tags.md)
