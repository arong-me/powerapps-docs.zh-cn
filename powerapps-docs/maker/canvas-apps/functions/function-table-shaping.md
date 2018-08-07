---
title: AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数 | Microsoft 文档
description: 有关 PowerApps 中 AddColumns、DropColumns、 RenameColumns 和 ShowColumns 函数的参考信息，包括语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 47e17c440e1bb0ae880769dabd9130fb10d3cbbe
ms.sourcegitcommit: 0f6d7bb9e524202c065b9a7ef92a7f54bdc4bc7c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39016205"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>PowerApps 中的 AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数
通过添加、删除、重命名和选择[表](../working-with-tables.md)的[列](../working-with-tables.md#columns)来为表造型。

## <a name="overview"></a>概述
以下函数通过调整表的列来为表造型：

* 将包含多个列的表缩减为包含一个列，使该表可用于 **[Lower](function-lower-upper-proper.md)** 或 **[Abs](function-numericals.md)** 等单列函数。  
* 将计算结果列（例如，显示“数量”乘以“单价”后的结果的“总价”列）添加到某个表。
* 使用更有意义的名称将列重命名，以便向用户显示或者在公式中使用。

表是 PowerApps 中的一个值，与字符串或数字类似。  可将表指定为公式中的参数，函数可以返回表作为结果。 本主题中介绍的函数不会修改表。 这些函数将表用作参数，并转换一个应用了转换的新表。  请参阅[使用表](../working-with-tables.md)，了解更多详情。  

无法使用这些函数修改[数据源](../working-with-data-sources.md)的列。 必须在数据源中修改数据。 可以使用 **[Collect](function-clear-collect-clearcollect.md)** 函数将列添加到[集合](../working-with-data-sources.md#collections)。  有关详细信息，请参阅[使用数据源](../working-with-data-sources.md)。  

## <a name="description"></a>描述
**AddColumns** 函数将列添加到表，某个公式将定义该列中的值。 现有列保持不变。

将会针对表的每条记录计算该公式。
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**DropColumns** 函数从表中排除列。  其他所有列保持不变。 **DropColumns** 排除列，**ShowColumns** 包含列。

**RenameColumns** 函数重命名表的列。 其他所有列保留其原始名称。

**ShowColumns** 函数包含某个表的列并删除其他所有列。 可以使用 **ShowColumns** 从多列表创建单列表。  **ShowColumns** 包含列，**DropColumns** 排除列。  

对于所有这些函数，结果是已应用转换的新表。  不会修改原始表。

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>语法
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要添加的列的名称。  必须为此参数指定字符串（例如 **"Name"**，包括双引号）。
* *Formula(s)* - 必需。  要针对每条记录计算的公式。 结果将添加为相应新列的值。 可在此公式中引用表的其他列。

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要删除的列的名称。 必须为此参数指定字符串（例如 **"Name"**，包括双引号）。

**RenameColumns**( *Table*, *OldColumneName*, *NewColumnName* )

* *Table* - 必需。  要运算的表。
* *OldColumnName* - 必需。 要重命名的列的名称。 此名称必须是字符串（例如 **"Name"**，包括双引号）。
* *NewColumnName* - 必需。 替换后的名称。 必须为此参数指定字符串（例如 **"Customer Name"**，包括双引号）。

**ShowColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要包含的列的名称。 必须为此参数指定字符串（例如 **"Name"**，包括双引号）。

## <a name="examples"></a>示例
本部分中的示例使用 **IceCreamSales** 数据源，其中包含下表中的数据：

![](media/function-table-shaping/icecream.png)

这些示例都不会修改 **IceCreamSales** 数据源。 每个函数将数据源的值转换为表，然后返回该值作为结果。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |将 **Revenue** 列添加到结果。  对于每条记录，将计算 **UnitPrice * QuantitySold**，并将结果放在新列中。 |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |从结果中排除 **UnitPrice** 列。 使用此函数可排除列，使用 **ShowColumns** 可包含列。 |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |仅在结果中包含 **Flavor** 列。 使用此函数可包含列，使用 **DropColumns** 可排除列。 |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |在结果中将 **UnitPrice** 列重命名。 |![](media/function-table-shaping/icecream-rename-price.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |从公式内部开始，按顺序执行以下表转换： <ol><li>根据针对每条记录计算 **UnitPrice * Quantity** 后的结果添加 **Revenue** 列。<li>将 **UnitPrice** 重命名为 **Price**。<li>排除 **Quantity** 列。</ol>  请注意，顺序很重要。 例如，不能在重命名 **UnitPrice** 后计算该列。 |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>分步操作
1. 导入或创建一个名为 **Inventory** 的集合，作为[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)中所述的第一个子过程。
2. 添加一个按钮，然后将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：
   
    **ClearCollect(Inventory2, RenameColumns(Inventory, "ProductName", "JacketID"))**
3. 按 F5，选择刚刚创建的按钮，然后按 Esc 返回设计工作区。
4. 在“文件”菜单中选择“集合”。
5. 确认已创建名为 **Inventory2** 的集合。 新集合包含的信息与 **Inventory**  相同，不过，**Inventory** 中名为 **ProductName** 的列在 **Inventory2** 中名为 **JacketID**。

