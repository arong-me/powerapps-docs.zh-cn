---
title: FilterExpression |Microsoft Docs
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
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
ms.openlocfilehash: 7b613238f28987b688d4f2299506fa91b72a99a7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343970"
---
# <a name="filterexpression"></a>FilterExpression

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="conditions"></a>条件和条款

与此筛选器关联的条件集。

**类型**： [ConditionExpression](conditionexpression.md)[]

### <a name="filteroperator"></a>filterOperator

用于合并此筛选器中的条件的运算符。

**类型**： `enum`

@No__t_0 值是具有以下可能值的枚举

|Value|成员|
|--|--|
|0|And|
|1|Or|

### <a name="filters"></a>筛选

评估此筛选器后应计算的任何子筛选器。

**类型**： [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)