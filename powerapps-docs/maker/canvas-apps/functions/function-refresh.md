---
title: "Refresh 函数 | Microsoft 文档"
description: "PowerApps 中 Refresh 函数的参考信息（包括语法和示例）"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 631b0c8fbfc98d73cf1d944c2a0f3933f8f10c11
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="refresh-function-in-powerapps"></a>PowerApps 中的 Refresh 函数
刷新[数据源](../working-with-data-sources.md)的[记录](../working-with-tables.md#records)。

## <a name="description"></a>说明
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

