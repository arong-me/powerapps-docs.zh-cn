---
title: Remove 和 RemoveIf 函数 | Microsoft 文档
description: PowerApps 中 Remove 和 RemoveIf 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 1baeebdff0edb728e18f7215ceacadb1317c33b8
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="remove-and-removeif-functions-in-powerapps"></a>PowerApps 中的 Remove 和 RemoveIf 函数
从[数据源](../working-with-data-sources.md)删除[记录](../working-with-tables.md#records)。

## <a name="description"></a>说明
### <a name="remove-function"></a>Remove 函数
使用 **Remove** 函数从数据源中删除特定的一个或多个记录。  

对于[集合](../working-with-data-sources.md#collections)来说，整个记录必须匹配。 可以使用 **All** 参数删除某个记录的所有副本；否则只会删除记录的一个副本。

### <a name="removeif-function"></a>RemoveIf 函数
使用 **RemoveIf** 函数根据一个或一组条件删除一个或多个记录。 每个条件都可以是其结果为 **true** 或 **false** 的任意公式，并且可以通过名称引用数据源的[列](../working-with-tables.md#columns)。 将会针对每个记录单独评估每个条件，如果所有条件的评估结果为 **true**，则会删除该记录。

**Remove** 和 **RemoveIf** 都以[表](../working-with-tables.md)的形式返回修改的数据源。 只能在[行为公式](../working-with-formulas-in-depth.md)中使用这两个函数。

还可使用 **[Clear](function-clear-collect-clearcollect.md)** 函数删除数据源中的所有记录。

### <a name="delegation"></a>委派
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>语法
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *DataSource* – 必需。 数据源，其中包含要删除的一个或多个记录。
* *Record(s)* - 必需。 要删除的一个或多个记录。
* **All** - 可选。 在集合中，同一记录可能出现多次。  添加 **All** 参数即可删除记录的所有副本。

**Remove**( *DataSource*, *Table* [, **All** ] )

* *DataSource* – 必需。 数据源，其中包含要删除的记录。
* *Table* - 必需。 要删除的记录表。
* **All** - 可选。 在集合中，同一记录可能出现多次。  添加 **All** 参数即可删除记录的所有副本。

**RemoveIf**( *DataSource*, *Condition* [, ... ] )

* *DataSource* – 必需。 数据源，其中包含要删除的一个或多个记录。
* *Condition(s)* - 必需。 一个公式，对于要删除的一个或多个记录，该公式的求值结果为 **true**。  可以在公式中使用 *DataSource* 中的列名。  如果指定多个 Conditions ，则所有 Conditions 的求值结果都必须为 **true**，然后才能删除一个或多个记录。

## <a name="examples"></a>示例
在以下示例中，你将删除某个数据源中的一个或多个记录。该数据源名为 **IceCream** 且以下表中的数据开头：

![](media/function-remove-removeif/icecream.png)

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |从数据源中删除 **Chocolate** 记录。 |<style> img { max-width: none } </style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>修改了 **IceCream** 数据源。 |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |从数据源中删除两个记录。 |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150 )** |删除其 **Quantity** 大于 **150** 的记录。 |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |删除其 **Quantity** 大于 150 且 **Flavor** 以 **S** 开头的记录。 |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, true )** |从数据源中删除所有记录。 |![](media/function-remove-removeif/icecream-empty.png)<br><br>修改了 **IceCream** 数据源。 |

### <a name="step-by-step"></a>分步操作
1. 导入或创建名为 **Inventory** 的集合，让其显示在库中，如[在库中显示数据](../show-images-text-gallery-sort-filter.md)所述。
2. 在库中，将图像的 **[OnSelect](../controls/properties-core.md)** 属性设置为以下表达式：<br>**Remove(Inventory, ThisItem)**
3. 按 F5，然后在库中选择图像。<br>从库和集合中删除项。

