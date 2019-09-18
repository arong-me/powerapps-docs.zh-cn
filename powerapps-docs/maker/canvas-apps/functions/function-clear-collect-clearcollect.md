---
title: Collect、Clear 和 ClearCollect 函数 | Microsoft 文档
description: PowerApps 中 Collect、Clear 和 ClearCollect 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2db3d31936329444746620e91e3414be914087d2
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038196"
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>PowerApps 中的 Collect、Clear 和 ClearCollect 函数

创建和清除[集合](../working-with-data-sources.md#collections)，以及将[记录](../working-with-tables.md#records)添加到任意[数据源](../working-with-data-sources.md)。

## <a name="description"></a>描述

### <a name="collect"></a>Collect

**Collect** 函数将记录添加到数据源。 可添加的项包括：

- 单个值：值将放入 **[值](function-value.md)** 新记录的字段。  所有其他属性保留为[空白](function-isblank-isempty.md)。
- A 记录：每个命名属性都放置在新记录的相应属性中。  所有其他属性保留为空白。
- [表](../working-with-tables.md)：表中的每条记录都作为数据源的单独记录添加，如上所述。 表不是以嵌套表形式添加到记录。 为实现此目的，需首先将表包装在记录中。

当用于集合时，将根据需要创建额外的[列](../working-with-tables.md#columns)。 该数据源将固定其他数据源的列，且无法添加新列。  

如果数据源尚不存在，则会创建一个集合。

集合有时可用于保留全局变量或作为数据源的临时副本。 PowerApps 以公式为基础，这些公式会在用户与应用交互时自动重新计算。 集合不具有此优势，并且使用这些集合可能会让应用更加难以进行创建和理解。 以此方式使用集合前，请查看[使用变量](../working-with-variables.md)。

还可使用 **[Patch](function-patch.md)** 函数在数据源中创建记录。

**Collect** 以表格形式返回修改后的数据源。  **Collect** 只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

### <a name="clear"></a>Clear

**Clear** 函数删除集合的所有记录。  集合的列将保留。

请注意，**Clear** 仅对集合执行运算，而不包括其他数据源。  鉴于此，可以使用 **[RemoveIf](function-remove-removeif.md)( *DataSource*, true )** 。  此函数将删除数据源存储中的所有记录并影响其他用户，请谨慎使用。

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

在以下示例中，将擦除名为 **IceCream** 的集合并向其进行添加。 数据源以下列内容开始：

![示例数据源](media/function-clear-collect-clearcollect/icecream.png)

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |清除 **IceCream** 集合中的所有数据，然后添加包含草莓冰淇淋数量的记录。 |<style>img {最大宽度：无}</style>![包含一条记录的表](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>还修改了**IceCream**集合。 |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |将两个记录添加到**IceCream**集合，该集合包含数量为 pistachio 和橙色的冰淇淋。 |![具有两条记录的表](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>还修改了**IceCream**集合。 |
| **Clear( IceCream )** |删除 **IceCream** 集合中的所有记录。 |![空表](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>还修改了**IceCream**集合。 |

有关如何创建集合的分步示例，请参阅[创建和更新集合](../create-update-collection.md)。

### <a name="records-and-tables"></a>记录和表

这些示例将检查如何处理要**收集**和**ClearCollect**的记录和表参数。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **ClearCollect （IceCream，{&nbsp;口味：&nbsp;"巧克力"，&nbsp;数量：&nbsp;100&nbsp;}，{&nbsp;口味：&nbsp;"Vanilla"，&nbsp;数量：&nbsp;200&nbsp;}  )** | 清除所有数据，然后将两个记录添加到**IceCream**集合，其中包括数量为巧克力和 vanilla 冰淇淋。  要添加的记录作为函数的各个参数提供。| ![添加到集合的巧克力和 Vanilla 记录](media/function-clear-collect-clearcollect/icecream.png) <br><br>还修改了**IceCream**集合。 |
| **ClearCollect （IceCream，Table （{&nbsp;口味：&nbsp;"巧克力"，&nbsp;数量：&nbsp;100&nbsp;}，{&nbsp;口味：&nbsp;"Vanilla"，&nbsp;数量：&nbsp;200&nbsp;}））** | 与前面的示例相同，不同之处在于，记录合并在一个表中，并通过单个自变量传入。 在将记录添加到**IceCream**集合之前，将按记录提取表的内容。 | ![添加到集合的巧克力和 Vanilla 记录](media/function-clear-collect-clearcollect/icecream.png)<br><br>还修改了**IceCream**集合。 |
| **ClearCollect （IceCream，<br>{&nbsp;MyFavorites：表（{&nbsp;口味：&nbsp;"Chocoalte"，&nbsp;数量：&nbsp;100&nbsp;}，{&nbsp;口味：&nbsp;"Vanilla"，&nbsp;数量：&nbsp;200&nbsp;} ) } )** | 与前面的示例相同，只是表包装在记录中。  不提取表的记录，而是将整个表作为记录的子表添加。 | ![添加到集合的巧克力和 Vanilla 记录](media/function-clear-collect-clearcollect/icecream-myfavorites.png)<br><br>还修改了**IceCream**集合。 |

