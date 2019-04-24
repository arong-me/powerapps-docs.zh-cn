---
title: AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数 | Microsoft 文档
description: 有关 PowerApps 中 AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数的参考信息，包括语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc682694bb22ecc63ecc762a735df07950ce29d3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61543632"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>PowerApps 中的 AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数
通过添加、删除、重命名和选择[表](../working-with-tables.md)的[列](../working-with-tables.md#columns)来为表造型。

## <a name="overview"></a>概述
以下函数通过调整表的列来为表造型：

* 将包含多个列的表缩减为包含一个列，使该表可用于 **[Lower](function-lower-upper-proper.md)** 或 **[Abs](function-numericals.md)** 等单列函数。  
* 将计算结果列（例如，显示“数量”乘以“单价”后的结果的“总价”列）添加到某个表。
* 使用更有意义的名称将列重命名，以便向用户显示或者在公式中使用。

表是 PowerApps 中的一个值，与字符串或数字类似。  可将表指定为公式中的参数，函数可以返回表作为结果。

> [!NOTE]
> 本主题介绍的函数不会修改原始表。 相反，此表作为参数，然后返回一个新的表应用了转换。 请参阅[使用表](../working-with-tables.md)，了解更多详情。  

无法使用这些函数修改[数据源](../working-with-data-sources.md)的列。 必须在数据源中修改数据。 可以使用 **[Collect](function-clear-collect-clearcollect.md)** 函数将列添加到[集合](../working-with-data-sources.md#collections)。 有关详细信息，请参阅[使用数据源](../working-with-data-sources.md)。  

## <a name="description"></a>描述
**AddColumns** 函数将列添加到表，某个公式将定义该列中的值。 现有列保持不变。

将会针对表的每条记录计算该公式。
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**DropColumns** 函数从表中排除列。  其他所有列保持不变。 **DropColumns** 排除列，**ShowColumns** 包含列。

使用 RenameColumns 函数重命名表的一个或多个列，方法是提供至少一个参数对，用于指定表包含的列的名称（要替换的旧名称）和表不包含的列的名称（要使用的新名称）。 旧名称必须已存在于表中，新名称不能存在。 每个列名在参数列表中只能出现一次，作为旧列名或新列名。 要将列重命名为现有列名，请先使用 DropColumns 删除现有列，或者通过在另一个函数中嵌套一个 RenameColumns 函数来重命名现有列。

**ShowColumns** 函数包含某个表的列并删除其他所有列。 可以使用 **ShowColumns** 从多列表创建单列表。  **ShowColumns** 包含列，**DropColumns** 排除列。  

对于所有这些函数，结果是已应用转换的新表。 不会修改原始表。 不能修改现有表的公式。 SharePoint、 Common Data Service、 SQL Server 和其他数据源修改的列的列表、 实体和表，这通常称为架构提供工具。 本主题中的函数仅转换输入的表，而无需修改原始，到输出表中供将来使用。

这些函数的参数支持委派。 例如，**筛选器**函数作为自变量用于拉入所有列表，将相关的记录搜索即使 **[dbo]。 [AllListings]** 数据源包含 100 万行：

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

但是，这些函数的输出都将遵守[非委派记录限制](../delegation-overview.md#non-delegable-limits)。  仅是 500 个记录返回在此示例中，即使**RealEstateAgents**数据源具有 501 或多个记录。

如果使用**AddColumns**以此方式**筛选器**必须为每个这些中的第一个记录进行单独调用数据源**RealEstateAgents**，这将导致大量的网络 chatter。 如果 **[dbo]。 [AllListings]** 够小且不会更改通常情况下，您可以调用**收集**函数，在[ **OnStart** ](signals.md#app)来缓存应用程序中的数据源启动时间。 作为替代方法，可以重构您的应用程序，以便仅当用户请求它们拉入相关的记录。  

## <a name="syntax"></a>语法
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要添加的列的名称。  必须为此参数指定字符串（例如 **"Name"**，包括双引号）。
* *Formula(s)* - 必需。  要针对每条记录计算的公式。 结果将添加为相应新列的值。 可在此公式中引用表的其他列。

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要删除的列的名称。 必须为此参数指定字符串（例如 **"Name"**，包括双引号）。

**RenameColumns**( *Table*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *OldColumnName* - 必需。 要从原始表重命名的列的名称。 此元素首先出现在参数对中（或者如果公式包含多个对，则首先出现在每个参数对中）。 此名称必须是字符串（例如 "Name"，包括双引号）。
* *NewColumnName* - 必需。 替换后的名称。 此元素最后出现在参数对中（或者如果公式包含多个对，则最后出现在每个参数对中）。 必须为此参数指定字符串（例如 "Customer Name"，包括双引号）。

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
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |重命名**UnitPrice**结果列。 |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |重命名结果中的 UnitPrice 和 QuantitySold 列。 |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |从公式内部开始，按顺序执行以下表转换： <ol><li>根据针对每条记录计算 **UnitPrice * Quantity** 后的结果添加 **Revenue** 列。<li>将 **UnitPrice** 重命名为 **Price**。<li>排除 **Quantity** 列。</ol>  请注意，顺序很重要。 例如，不能在重命名 **UnitPrice** 后计算该列。 |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>分步操作

让我们尝试从本主题中前面的示例。  

1. 通过添加创建集合**[按钮](../controls/control-button.md)** 控件并设置其**OnSelect**属性设为此公式：

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. 通过在按住 Alt 键的同时选择的按钮运行该公式。

1. 添加另一个**按钮**控件，将其**OnSelect**属性设为此公式，然后运行它：

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. 上**文件**菜单中，选择**集合**，然后选择**IceCreamSales**以显示该集合。
 
    如图所示，第二个公式不修改此集合。 **AddColumns**使用函数**IceCreamSales**作为只读的参数; 该函数未修改该参数所引用的表。
    
    ![显示冰激销售额集合中不包含收入列的三条记录的集合查看器](media/function-table-shaping/ice-cream-sales-collection.png)

1. 选择**FirstExample**。

    如图所示，第二个公式将返回具有添加的列的新表。 **ClearCollect**函数捕获中的新表**FirstExample**集合，将一些内容添加到原始表，因为它不修改源流动函数：

    ![显示包含新的收入列的第一个示例集合的三条记录的集合查看器](media/function-table-shaping/first-example-collection.png)
