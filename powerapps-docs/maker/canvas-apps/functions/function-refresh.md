---
title: Refresh 函数 | Microsoft 文档
description: PowerApps 中 Refresh 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72fafd2b55237dc4804c50c26530fddb763d9623
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984285"
---
# <a name="refresh-function-in-powerapps"></a>PowerApps 中的 Refresh 函数
刷新[数据源](../working-with-data-sources.md)的[记录](../working-with-tables.md#records)。

## <a name="description"></a>描述
**Refresh** 函数检索数据源的新副本。  你将看到其他用户所做的更改。

**Refresh** 没有返回值，只可以在[行为公式](../working-with-formulas-in-depth.md)中使用它。

## <a name="syntax"></a>语法
**Refresh**( DataSource )

* *DataSource* – 必需。 要刷新的数据源。

## <a name="example"></a>示例
在此示例中，你将将刷新名为 **IceCream** 的数据源，该数据源以下面的数据开头：

![](media/function-refresh/icecream.png)

另一个设备上的用户将 **Strawberry** 记录中的**数量**更改为 **400**。  此值将保持不变，直到执行以下公式：

**Refresh( IceCream )**

执行此公式后，绑定到 **IceCream** 数据源的库将显示 **Strawberry** 更新后的值：

![](media/function-refresh/icecream-after.png)

