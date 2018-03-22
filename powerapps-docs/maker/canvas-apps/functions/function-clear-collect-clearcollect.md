---
title: "Collect、Clear 和 ClearCollect 函数 | Microsoft 文档"
description: "PowerApps 中 Collect、Clear 和 ClearCollect 函数的引用信息（包括语法和示例）"
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
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: cc12241861a1dd6a0242810bb1a6faab70a2de27
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>PowerApps 中的 Collect、Clear 和 ClearCollect 函数
创建和清除[集合](../working-with-data-sources.md#collections)，以及将[记录](../working-with-tables.md#records)添加到任意[数据源](../working-with-data-sources.md)。

## <a name="description"></a>说明
### <a name="collect"></a>Collect
**Collect** 函数将记录添加到数据源。 可添加的项包括：

* 单个值：该值置于新记录的 **[Value](function-value.md)** 字段中。  所有其他属性保留为[空白](function-isblank-isempty.md)。
* 记录：每个命名属性都置于新记录的对应属性中。  所有其他属性保留为空白。
* [表](../working-with-tables.md)：如上所述，表中的每条记录将作为数据源的单个记录添加。 表不是以嵌套表形式添加到记录。 为实现此目的，需首先将表包装在记录中。

当用于集合时，将根据需要创建额外的[列](../working-with-tables.md#columns)。 该数据源将固定其他数据源的列，且无法添加新列。  

如果数据源尚不存在，则会创建一个集合。

集合有时可用于保留全局变量或作为数据源的临时副本。 PowerApps 以公式为基础，这些公式会在用户与应用交互时自动重新计算。 集合不具有此优势，并且使用这些集合可能会让应用更加难以进行创建和理解。 以此方式使用集合前，请查看[使用变量](../working-with-variables.md)。

还可使用 **[Patch](function-patch.md)** 函数在数据源中创建记录。

**Collect** 以表格形式返回修改后的数据源。  **Collect** 只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

### <a name="clear"></a>Clear
**Clear** 函数删除集合的所有记录。  集合的列将保留。

请注意，**Clear** 仅对集合执行运算，而不包括其他数据源。  鉴于此，可以使用 **[RemoveIf](function-remove-removeif.md)( *DataSource*, true )**。  此函数将删除数据源存储中的所有记录并影响其他用户，请谨慎使用。

可使用 **[Remove](function-remove-removeif.md)** 函数选择性地删除记录。

**Clear** 没有返回值。  只能在行为公式中使用。

### <a name="clearcollect"></a>ClearCollect
**ClearCollect** 函数删除集合中的所有记录，并向同一集合添加一组不同的记录。  **ClearCollect** 这单个函数可提供 **Clear** 和 **Collect** 的组合功能。

**ClearCollect** 以表格形式返回修改后的集合。  **ClearCollect** 只能在行为公式中使用。

## <a name="syntax"></a>语法
**Collect**( *DataSource*, *Item*, ... )

* *DataSource* – 必需。 要向其添加数据的数据源。  如果尚不存在，将创建一个新的集合。
* *Item(s)* - 必需。  要添加到数据源的一个或多个记录或表。  

**Clear**( *Collection* )

* *Collection* - 必需。 要清除的集合。

**ClearCollect**( *Collection*, *Item*, ... )

* *Collection* - 必需。 要清除然后向其添加数据的集合。
* *Item(s)* - 必需。  要添加到数据源的一个或多个记录或表。  

## <a name="examples"></a>示例
### <a name="clearing-and-adding-records-to-a-data-source"></a>清除并将记录添加到数据源
在以下示例中，将擦除名为 **IceCream** 的集合并向其进行添加。  数据源以下列内容开始：

![](media/function-clear-collect-clearcollect/icecream.png)

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |清除 **IceCream** 集合中的所有数据，然后添加包含草莓冰淇淋数量的记录。 |<style> img { max-width: none } </style> ![](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>**IceCream** 数据源也已得到修改。 |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |向 **IceCream** 集合添加两条记录，其中包括开心果味冰淇淋和橙子味冰淇淋的数量。 |![](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>**IceCream** 数据源也已得到修改。 |
| **Clear( IceCream )** |删除 **IceCream** 集合中的所有记录。 |![](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>**IceCream** 数据源也已得到修改。 |

### <a name="step-by-step"></a>分步操作
1. 添加一个按钮，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下函数：<br>**Collect(Products, &quot;Europa&quot;, &quot;Ganymede&quot;, &quot;Callisto&quot;)**
   
    此函数创建名为 **Products** 的集合，其中包含对应每一个（共三个）产品名的行。
2. 按 F5，单击按钮，然后按 Esc 键返回设计工作区。
3. （可选）若要显示所创建集合的预览，请单击“内容”选项卡上的“集合”。

