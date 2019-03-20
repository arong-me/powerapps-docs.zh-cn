---
title: ForAll 函数 | Microsoft 文档
description: PowerApps 中 ForEach 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f538d785b9655b94a44a79c3299e979bbfe88883
ms.sourcegitcommit: ba5542ff1c815299baa16304c6e0b5fed936e776
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54308768"
---
# <a name="forall-function-in-powerapps"></a>PowerApps 中的 ForAll 函数
针对[表](../working-with-tables.md)中的所有[记录](../working-with-tables.md#records)计算值和执行操作。

## <a name="description"></a>说明
**ForAll** 函数针对表中的所有记录对公式求值。  该公式可以计算值并/或执行操作，例如修改数据或使用连接。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

### <a name="return-value"></a>返回值
每个公式求值的结果都在表中返回，并采用与输入表相同的顺序。

如果公式的结果是单个值，则结果表将是一个单列表。  如果公式的结果是一条记录，则结果表将包含与结果记录具有相同列的记录。  

如果公式的结果是*空*值，则结果表中将没有与该该输入记录对应的记录。  在这种情况下，结果表中的记录数将少于源表中的记录数。

### <a name="taking-action"></a>执行操作
公式可以包含用于执行操作的函数，例如使用 **[Patch](function-patch.md)** 和 **[Collect](function-clear-collect-clearcollect.md)** 函数修改数据源的记录。  公式还可以调用针对连接的方法。  可以通过使用 [**;** 运算符](operators.md)对每条记录执行多个操作。 无法修改作为 **ForAll** 函数的使用者的表。

在编写公式时，请记住，可以按任何顺序处理记录，并且有可能可以并行处理。  可以在表的最后一条记录后处理第一条记录。  请小心避免使用排序依赖关系。  因此，你不能在 **ForAll** 函数内使用使用 **[UpdateContext](function-updatecontext.md)**、**[Clear](function-clear-collect-clearcollect.md)** 和 **[ClearCollect](function-clear-collect-clearcollect.md)** 函数，因为它们很容易用来存放易受此效果影响的变量。  你可以使用 **[Collect](function-clear-collect-clearcollect.md)**，但添加记录的顺序是不确定的。

多个可修改数据源的函数（包括 **Collect**、**Remove** 和 **Update**）会将更改后的数据源作为其返回值来返回。  如果针对 **ForAll** 表的每条记录进行返回，则这些返回值可能很大并占用大量资源。  你还可能会发现这些返回值不是你想要的，因为 **ForAll** 可以并行操作并且可能会将这些函数的副作用与获取其结果分离开来。  幸运的是，如果来自 **ForAll** 的返回值实际上未使用（对于数据修改函数这是常见情况），则不会创建返回值，因此不需要考虑资源或排序。  但是，如果你使用 **ForAll** 的结果并且使用了返回数据源的函数之一，请仔细考虑如何安排结果的结构并首先针对小型数据集进行测试。  

### <a name="alternatives"></a>替代方法
PowerApps 中的许多函数可以通过使用单列表一次处理多个值。  例如，**Len** 函数可以采用与 **ForAll** 相同的方式处理包含文本值的表，返回包含长度的表。  这样，在很多情况下将不需要使用 **ForAll**，因此可以更高效并且更容易阅读。

另一个需要注意的事项是 **ForAll** 不可委派，而诸如 **Filter** 之类的其他函数则可以。  

### <a name="delegation"></a>委派
[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>语法
**ForAll**( *Table*, *Formula* )

* *Table* - 必需。 要对其执行操作的表。
* *Formula* - 必需。  用于对 *Table* 中的所有记录进行求值的公式。

## <a name="examples"></a>示例
### <a name="calculations"></a>计算
以下示例使用 **Squares** [数据源](../working-with-data-sources.md)：

![](media/function-forall/squares.png)

若要将此数据源创建为集合，请将某个**按钮**控件的 **OnSelect** 属性设置为以下公式，打开“预览”模式，然后单击或点击按该钮：

`ClearCollect( Squares, [ "1", "4", "9" ] )`

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **ForAll(&nbsp;Squares, Sqrt(&nbsp;Value&nbsp;)&nbsp;)**<br><br>**Sqrt(&nbsp;Squares&nbsp;)** |针对输入表中的所有记录计算 **Value** 列的平方根。  **Sqrt** 函数还可以与单列表一起使用，从而可以在不使用 **ForAll** 的情况下执行此示例。 |<style> img { max-width: none } </style> ![](media/function-forall/sqrt.png) |
| **ForAll(&nbsp;Squares, Power(&nbsp;Value,&nbsp;3&nbsp;)&nbsp;)** |针对输入表中的所有记录计算 **Value** 列的三次幂。  **Power** 函数不支持单列表。 因此，在本例中必须使用 **ForAll**。 |<style> img { max-width: none } </style> ![](media/function-forall/power3.png) |

### <a name="using-a-connection"></a>使用连接
以下示例使用 **Expressions** [数据源](../working-with-data-sources.md)：

![](media/function-forall/translate.png)

若要将此数据源创建为集合，请将某个**按钮**控件的 **OnSelect** 属性设置为以下公式，打开“预览”模式，然后单击或点击按该钮：

`ClearCollect( Expressions, [ "Hello", "Good morning", "Thank you", "Goodbye" ] )`

此示例还使用一个 [Microsoft Translator](../connections/connection-microsoft-translator.md) 连接。  若要将此连接添加到你的应用，请参阅有关如何[管理连接](../add-manage-connections.md)的主题。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "es" ) )** |针对 Expressions 表中的所有记录将 **Value** 列的内容翻译为西班牙语（缩写为“es”）。 |<style> img { max-width: none } </style> ![](media/function-forall/translate-es.png) |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "fr" ) )** |针对 Expressions 表中的所有记录将 **Value** 列的内容翻译为法语（缩写为“fr”）。 |<style> img { max-width: none } </style> ![](media/function-forall/translate-fr.png) |

### <a name="copying-a-table"></a>复制表
有时候，你需要对数据进行筛选、整形、排序和操作。  PowerApps 提供了许多用于执行这些操作的函数，例如 **Filter**、**AddColumns** 和 **Sort**。  PowerApps 将每个表视为一个值，允许它在公式中流动和并可轻松使用。      

有时候，你希望创建此结果的副本供以后使用。  或者，你可能希望将信息从一个数据源移动到另一个数据源。  PowerApps 提供了 **Collect** 函数来复制数据。

但是，在创建该副本之前，请仔细考虑是否确实需要该副本。  许多情况可以通过按需使用公式对基础数据源进行筛选和整形来解决。 创建副本的一些不利影响包括：

* 同一信息存在两个副本意味着它们有可能不同步。  
* 创建副本会消耗大量的计算机内存、网络带宽和/或时间。  
* 对于大多数数据源，复制无法委派，这限制了可以移动的数据量。      

以下示例使用 **Products** [数据源](../working-with-data-sources.md)：

![](media/function-forall/prod.png)

若要将此数据源创建为集合，请将某个**按钮**控件的 **OnSelect** 属性设置为以下公式，打开“预览”模式，然后单击或点击按该钮：

```powerapps-dot
ClearCollect( Products, 
    Table( 
        { Product: "Widget",    'Quantity Requested': 6,  'Quantity Available': 3 }, 
        { Product: "Gadget",    'Quantity Requested': 10, 'Quantity Available': 20 },
        { Product: "Gizmo",     'Quantity Requested': 4,  'Quantity Available': 11 },
        { Product: "Apparatus", 'Quantity Requested': 7,  'Quantity Available': 6 } 
    )
)
```

我们的目标是使用一个派生表，使其中仅包含所请求数量大于可用数量并且我们需要订购的商品：

![](media/function-forall/prod-order.png)  

我们可以通过几种不同的方法执行此操作，所有这些方法都生成相同的结果，各有优缺点。

#### <a name="table-shaping-on-demand"></a>按需进行表整形
不要创建该副本！  我们可以在有需要的任何位置使用以下公式：

```powerapps-dot
// Table shaping on demand, no need for a copy of the result
ShowColumns( 
    AddColumns( 
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
    ), 
    "Product", 
    "Quantity To Order"
)
```

**Filter** 和 **AddColumns** 函数分别会创建一个[记录范围](../working-with-tables.md#record-scope)来使用每条记录的 **'Quantity Requested'** 和 **'Quantity Available'** 字段执行比较和减法操作。

在此示例中，**Filter** 函数可以委派。  这非常重要，因为它可以找到符合条件的所有产品，即使表中的数百万产品中只有少数产品符合条件也是如此。  同时，**ShowColumns** 和 **AddColumns** 无法委派，因此，需要订购的实际产品数量将是有限的。  如果你知道此结果的大小始终比较小，则此方法很合适。

并且，因为我们没有创建副本，因此该信息没有额外的副本需要管理或者会过期。  

#### <a name="forall-on-demand"></a>按需 ForAll
另一种方法是使用 **ForAll** 函数来替换表整形函数：

```powerapps-dot
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        { 
            Product: Product, 
            'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
        } 
    ) 
)
```

对某些人来说，此公式可能更容易阅读和编写。

**ForAll** 的任何部件都不可委派。  只会对 **Products** 表的第一部分进行评估，如果此表非常大，这可能是一个问题。  因为 **Filter** 在上一示例中是可委派的，因此它可能更适用于大型数据集。

#### <a name="collect-the-result"></a>收集结果
在某些情况下，可能需要数据的副本。  你可能需要将信息从一个数据源移动到另一个数据源。  在此示例中，订单是通过供应商的系统上的 **NewOrder** 表下达的。  为实现高速用户交互，你可能希望缓存表的一个本地副本以便消除服务器延迟。

我们使用与前面的两个示例相同的表整形，但是将结果捕获到一个集合中：

```powerapps-dot
ClearCollect( NewOrder, 
    ShowColumns( 
        AddColumns( 
            Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
            "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
        ), 
        "Product", 
        "Quantity To Order"
    )
)
```

```powerapps-dot
ClearCollect( NewOrder, 
    ForAll( Products, 
        If( 'Quantity Requested' > 'Quantity Available', 
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        } 
    )
)
```

**ClearCollect** 和 **Collect** 无法委派。  因此，可以通过此方式移动的数据量是有限的。

#### <a name="collect-within-forall"></a>ForAll 内的 Collect
最后，我们可以直接在 **ForAll** 内执行 **Collect**：

```powerapps-dot
Clear( ProductsToOrder ); 
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        Collect( NewOrder,  
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        )
    )
)
```

同样，**ForAll** 函数此时无法委派。  如果我们的 **Products** 表很大，则**ForAll** 将仅查找第一组记录，我们可能会错过一些需要订购的产品。  但是，对于我们知道一直会比较小的表，此方法很合适。

注意，我们未捕获 **ForAll** 的结果。  从其中调用的 **Collect** 函数将返回所有记录的 **NewOrder** 数据源，如果我们捕获结果，这可能会增加大量的数据。  

