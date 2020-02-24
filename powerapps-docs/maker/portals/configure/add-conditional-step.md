---
title: 为门户配置条件步骤类型 | MicrosoftDocs
description: 有关如何添加和配置门户的条件步骤类型的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 698f2e16cdefee0708acbcbd413a1c229a577839
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979633"
---
# <a name="add-a-conditional-step-type"></a>添加条件步骤类型

Web 窗体步骤可以为指示步骤应评估表达式的“条件”类型。 如果表达式评估为 true，那么下一步将显示。 如果表达式评估为 false，并且已指定“如果条件失败进行下一步”，该步骤将显示。 当前实体为用于依照其评估表达式的目标。 记录源默认为先前步骤的记录源。

## <a name="attributes"></a>属性

| 客户                         | 说明                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 条件                    | 要评估的条件表达式                                                                                                                                                                                           |
| 不满足条件时的下一步 | 条件步骤类型与所有其他类型不同，有两个“下一步”查找。 如果条件评估为 true，默认“下一步”查找将使用。 此属性设置下一步应将条件评估为 false。 |

可用操作数如下所示：

| 操作数    | Type                   |
|---------------|------------------------|
| =, ==         | 等于                 |
| !=            | 不等于             |
| &gt;          | 大于           |
| &lt;          | 小于              |
| &gt;=         | 大于或等于 |
| &lt;=         | 小于或等于    |
| &             | 和                    |
| \|             | 或                     |
| !             | 不                    |
| =\*、==\*、-= | 相似                   |
| !=\*          | 不相似               |

## <a name="format"></a>格式

表达式的格式如下：

\[实体属性逻辑名称\] \[操作数\] \[值\]

示例：

new\_categorycode = 750101

条件可以具有多个表达式。 可以使用用括号组合嵌套表达式，例如：

new\_categorycode = 750101 & gendercode = 2

-   new\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   new\_name = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体窗体](entity-forms.md)  
[门户的 Web 窗体步骤](web-form-steps.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[重定向步骤类型](add-redirect-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

