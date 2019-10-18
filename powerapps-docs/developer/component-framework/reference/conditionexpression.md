---
title: ConditionExpression | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
ms.openlocfilehash: 10f7275643c0df4c2a4099a80b490fb5e27ce318
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345534"
---
# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="attributename"></a>attributeName

要对其应用筛选器的数据集列的名称。

**类型**： `string`

### <a name="conditionoperator"></a>conditionOperator

用于计算条件的运算符。

**类型**： `enum`

@No__t_0 值是具有以下可能值的枚举

|Value|成员|
|--|--|
|-1|内容|
|0|=|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|GreaterEqual|
|5|LessEqual|
|6|外观|
|8|In|
|12|无效|
|14|昨天|
|15|Today|
|超过|致力|
|11x17|Last7Days|
|18|Next7Days|
|19|LastWeek|
|0\.2|本周|
|22|LastMonth|
|23|ThisMonth|
|25|基于|
|得到|OnOrBefore|
|日|OnOrAfter|
|28|LastYear|
|5|ThisYear|
|33|LastXDays|
|34|NextXDays|
|37|LastXMonths|
|38|NextXMonths|
|49|有|
|70|InFiscalPeriodAndYear|
|75|上述|
|76|下|
|77|NotUnder|
|78|AboveOrEqual|
|79|UnderOrEqual|
|87|ContainValues|

### <a name="entityaliasname"></a>entityAliasName

实体别名，以便可以在链接的实体上使用筛选。

**类型**： `string`

### <a name="value"></a>值

由条件计算的值。

**类型**： `string | string[]`

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)