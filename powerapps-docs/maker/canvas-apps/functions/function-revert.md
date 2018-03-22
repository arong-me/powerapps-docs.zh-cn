---
title: "Revert 函数 | Microsoft 文档"
description: "PowerApps 中 Revert 函数的参考信息（包括语法和示例）"
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
ms.openlocfilehash: e61566077ccdf9f3b2913ec0293868c1863c26fa
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="revert-function-in-powerapps"></a>PowerApps 中的 Revert 函数
刷新[数据源](../working-with-data-sources.md)的[记录](../working-with-tables.md#records)并清除错误。

## <a name="description"></a>说明
**Revert** 函数可用于刷新整个数据源或者数据源中的单个记录。 这样你就可以看到其他用户进行的更改。

对于还原的记录，**Revert** 还可以从返回了 **[Errors](function-errors.md)** 函数的[表](../working-with-tables.md)中清除所有错误。

如果 **[Errors](function-errors.md)** 函数在执行 **[Patch](function-patch.md)** 或其他数据操作后报告了冲突，则**还原**记录，从冲突版本开始并重新应用更改。

**Revert** 函数没有返回值。 只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

## <a name="syntax"></a>语法
**Revert**( *DataSource* [, *Record* ] )

* *DataSource* – 必需。 要还原的数据源。
* *Record* - 可选。  要还原的记录。  如果不指定记录，则会还原整个数据源。

## <a name="example"></a>示例
在本例中，你将还原名为 **IceCream** 的数据源，这个数据源刚开始包含下表中的数据：

![](media/function-revert/icecream.png)

另一个设备上的用户将 **Strawberry** 记录的 **Quantity** 属性改成了 **400**。  几乎在同一时间，你将同一条记录的同一个属性改成了 **500**，但不知道他人也进行了更改。

随后你使用 **[Patch](function-patch.md)** 函数更新记录：<br>
**Patch( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ), { Quantity: 500 } )**

当你检查 **[Errors](function-errors.md)** 表时，发现了如下错误：

| 记录 | [列](../working-with-tables.md#columns) | 消息 | 错误 |
| --- | --- | --- | --- |
| **{ ID: 1, Flavor: "Strawberry", Quantity: 300 }** |*blank* |**“另一个用户修改了你尝试修改的记录。请还原记录，然后重试。”** |**ErrorKind.Conflict** |

根据 **Error** 列中的内容，你可以看到一个“重新加载”按钮，其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

选择“重新加载”按钮后，**[Errors](function-errors.md)** 表变为[空白](function-isblank-isempty.md)，并且 **Strawberry** 的新值已加载：

![](media/function-revert/icecream-after.png)

完成上述更改之后，你重新应用了更改，这次成功了，因为已经解决了冲突。

![](media/function-revert/icecream-success.png)

