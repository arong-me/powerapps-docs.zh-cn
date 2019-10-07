---
title: AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数 | Microsoft 文档
description: 有关 PowerApps 中 AddColumns、DropColumns、RenameColumns 和 ShowColumns 函数的参考信息，包括语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6f2dfae897a19c66e493cbdecd897df87b8194c2
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992215"
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
> 本主题描述的函数不会修改原始表。 相反，它们将该表作为参数，并返回一个应用了转换的新表。 请参阅[使用表](../working-with-tables.md)，了解更多详情。  

无法使用这些函数修改[数据源](../working-with-data-sources.md)的列。 必须在数据源中修改数据。 可以使用 **[Collect](function-clear-collect-clearcollect.md)** 函数将列添加到[集合](../working-with-data-sources.md#collections)。 有关详细信息，请参阅[使用数据源](../working-with-data-sources.md)。  

## <a name="description"></a>描述
**AddColumns** 函数将列添加到表，某个公式将定义该列中的值。 现有列保持不变。

将会针对表的每条记录计算该公式。
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**DropColumns** 函数从表中排除列。  其他所有列保持不变。 **DropColumns** 排除列，**ShowColumns** 包含列。

使用RenameColumns 函数重命名表的一个或多个列，方法是提供至少一个参数对，用于指定表包含的列的名称（要替换的旧名称）和表不包含的列的名称（要使用的新名称）。 旧名称必须已存在于表中，新名称不能存在。 每个列名在参数列表中只能出现一次，作为旧列名或新列名。 要将列重命名为现有列名，请先使用DropColumns 删除现有列，或者通过在另一个函数中嵌套一个RenameColumns 函数来重命名现有列。

**ShowColumns** 函数包含某个表的列并删除其他所有列。 可以使用 **ShowColumns** 从多列表创建单列表。  **ShowColumns** 包含列，**DropColumns** 排除列。  

对于所有这些函数，结果是已应用转换的新表。 不会修改原始表。 不能使用公式来修改现有表。 SharePoint、Common Data Service、SQL Server 和其他数据源提供了修改列表、实体和表（通常称为架构）的列的工具。 本主题中的函数只转换输入表，而不将原始表修改为输出表以供进一步使用。

这些函数的参数支持委托。 例如，用作参数的**筛选器**函数在所有列表中进行搜索，即使 **"[dbo]. [AllListings] "** 数据源包含一百万行：

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

但是，这些函数的输出受[非委托记录限制的限制](../delegation-overview.md#non-delegable-limits)。  在此示例中，即使**RealEstateAgents**数据源包含501个或更多记录，也只返回500个记录。

如果以这种方式使用**AddColumns** ，则**筛选器**必须对**RealEstateAgents**中的第一条记录进行单独的数据源调用，这会导致大量网络 chatter。 如果为 **[dbo]. [AllListings]** 非常小并且不经常更改，你可以在[**OnStart**](signals.md#app)中调用**Collect**函数，以便在应用启动时在应用中缓存数据源。 作为替代方法，你可以重新构建你的应用程序，以便仅在用户请求时才请求相关记录。  

## <a name="syntax"></a>语法
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要添加的列的名称。  必须为此参数指定字符串（例如 **"Name"** ，包括双引号）。
* *Formula(s)* - 必需。  要针对每条记录计算的公式。 结果将添加为相应新列的值。 可在此公式中引用表的其他列。

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要删除的列的名称。 必须为此参数指定字符串（例如 **"Name"** ，包括双引号）。

**RenameColumns**（ *Table*， *OldColumnName1*， *NewColumnName1* [， *OldColumnName2*， *NewColumnName2*，...]）

* *Table* - 必需。  要运算的表。
* *OldColumnName* - 必需。 要从原始表重命名的列的名称。 此元素首先出现在参数对中（或者如果公式包含多个对，则首先出现在每个参数对中）。 此名称必须是字符串（例如 "Name"，包括双引号）。
* *NewColumnName* - 必需。 替换后的名称。 此元素最后出现在参数对中（或者如果公式包含多个对，则最后出现在每个参数对中）。 必须为此参数指定字符串（例如 "Customer Name"，包括双引号）。

**ShowColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必需。  要运算的表。
* *ColumnName(s)* - 必需。 要包含的列的名称。 必须为此参数指定字符串（例如 **"Name"** ，包括双引号）。

## <a name="examples"></a>示例
本部分中的示例使用 **IceCreamSales** 数据源，其中包含下表中的数据：

![](media/function-table-shaping/icecream.png)

这些示例都不会修改 **IceCreamSales** 数据源。 每个函数将数据源的值转换为表，然后返回该值作为结果。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |将 **Revenue** 列添加到结果。  对于每条记录，将计算 **UnitPrice * QuantitySold**，并将结果放在新列中。 |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |从结果中排除 **UnitPrice** 列。 使用此函数可排除列，使用 **ShowColumns** 可包含列。 |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |仅在结果中包含 **Flavor** 列。 使用此函数可包含列，使用 **DropColumns** 可排除列。 |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |重命名结果中的 "**单价**" 列。 |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |重命名结果中的 UnitPrice 和 QuantitySold 列。 |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |从公式内部开始，按顺序执行以下表转换： <ol><li>根据针对每条记录计算 **UnitPrice * Quantity** 后的结果添加 **Revenue** 列。<li>将 **UnitPrice** 重命名为 **Price**。<li>排除 **Quantity** 列。</ol>  请注意，顺序很重要。 例如，不能在重命名 **UnitPrice** 后计算该列。 |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>分步操作

接下来，请尝试本主题前面部分中的一些示例。  

1. 通过添加 **[按钮](../controls/control-button.md)** 控件并将其**OnSelect**属性设置为以下公式来创建集合：

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. 通过在按住 Alt 键的同时选择 "" 按钮来运行该公式。

1. 添加第二个**按钮**控件，将其**OnSelect**属性设置为此公式，然后运行它：

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. 在 "**文件**" 菜单上，选择 "**集合**"，然后选择 " **IceCreamSales** " 以显示该集合。
 
    如图所示，第二个公式未修改此集合。 **AddColumns**函数将**IceCreamSales**用作只读参数;函数未修改该参数所引用的表。
    
    ![集合查看器显示了三个不包括收入列的冰淇淋销售集合记录](media/function-table-shaping/ice-cream-sales-collection.png)

1. 选择**FirstExample**。

    如图所示，第二个公式返回了一个新表，其中包含添加的列。 **ClearCollect**函数捕获**FirstExample**集合中的新表，并在其流过函数时向原始表添加一些内容，而无需修改源：

    ![集合查看器，显示第一个示例集合的三个记录，其中包含新的收入列](media/function-table-shaping/first-example-collection.png)
