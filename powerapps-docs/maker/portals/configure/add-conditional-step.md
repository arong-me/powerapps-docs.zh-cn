---
title: 为门户配置条件步骤类型 |MicrosoftDocs
description: 有关为门户添加和配置条件步骤类型的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ec3e568b239bf66c0d4554e244d5afef2d5ef673
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553661"
---
# <a name="add-a-conditional-step-type"></a>添加条件步骤类型

Web 窗体步骤可以是 "Condition" 类型，它表示步骤应计算表达式。 如果表达式的计算结果为 true，则显示下一步。 如果表达式的计算结果为 false，并且指定了 "下一步条件失败"，则将显示该步骤。 当前实体是用于对表达式进行计算的目标。 记录源默认为上一步的记录源。

## <a name="attributes"></a>特性

| 名称                         | 描述                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 状态                    | 要计算的条件表达式                                                                                                                                                                                           |
| 条件失败时的下一步 | 与所有其他条件不同，条件步骤类型具有两个后续步骤查找。 如果条件的计算结果为 true，则将遵守默认的下一步查找。 此属性设置条件的计算结果为 false 时的下一步。 |

可用的操作数如下：

| 操作数    | 类型                   |
|---------------|------------------------|
| =, ==         | 对应                 |
| !=            | 不等于             |
| &gt;          | 大于           |
| &lt;          | 小于              |
| &gt;=         | 大于或等于 |
| &lt;=         | 小于或等于    |
| &             | And                    |
| \|             | Or                     |
| !             | 否                    |
| =\*，= =\*，-= | 外观                   |
| ！ =\*          | 不类似于               |

## <a name="format"></a>格式

表达式的格式如下所示：

\[实体属性逻辑名称\] \[操作数\] \[值\]

示例：

new\_categorycode = 750101

一个条件可以有多个表达式。 可以使用括号将嵌套表达式分组，例如：

new\_categorycode = 750101 & gendercode = 2

-   new\_categorycode = 750101 & （gendercode = 2 | gendercode = 3）

-   新\_名称 = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体窗体](entity-forms.md)  
[门户的 Web 窗体步骤](web-form-steps.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[重定向步骤类型](add-redirect-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

