---
title: "了解委派 | Microsoft 文档"
description: "使用委派高效处理大型数据集。"
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
ms.date: 08/15/2017
ms.author: gregli
ms.openlocfilehash: b6410a6b392f074c5e5a240e471fa2591e1e135d
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="understand-delegation"></a>了解委派
PowerApps 包括一组用于数据表筛选、排序和整理的功能强大的函数：**[Filter](functions/function-filter-lookup.md)**、**[Sort](functions/function-sort.md)**、**[AddColumns](functions/function-table-shaping.md)**，等等。  可以使用这些函数，让用户重点访问其所需的信息。  对于具有数据库背景的用户来说，使用这些函数相当于编写数据库查询。  

若要生成有效的应用，关键是尽量减少需要转到设备的数据量。  也许在成千上万条记录中，只需要少量记录；也许单个聚合值就可以代表数千条记录；  也许只有第一组记录可以检索，而其余记录是用户在需要更多记录的情况下通过笔势输入的。  进行重点访问可以大幅缩减应用所需的处理能力、内存和网络带宽，提高用户的响应速度，即使使用的是通过移动电话网络连接的手机。  

若要通过 PowerApps 公式来尽量减少通过网络传输的数据，则需使用“委派”。  简而言之，这意味着，PowerApps 会将数据的处理委派给数据源，而不是将数据移到应用进行本地处理。  

但这会很复杂，这也是写作本文的原因，因为并非所有能够在 PowerApps 公式中表示的内容都可以委派给所有数据源。  PowerApps 语言与 Excel 的公式语言类似，旨在让用户能够完整且即时地访问内存中的整个工作簿，并且提供各种数字和文本操作函数。  因此，PowerApps 语言要比大多数数据源能够支持的语言（包括强大的数据库引擎，例如 SQL Server）丰富得多。

**处理大型数据集需要使用数据源和能够委派的公式。**  若要让应用始终运行良好，同时要确保用户能够访问所需的全部信息，这是唯一的方式。 请注意[蓝点建议](delegation-overview.md#blue-dot-suggestions)，这表示不能使用委派的地方。  如果处理的是小型数据集（不到 500 条记录），则可使用任何数据源和公式，因为在公式不能委派的情况下，可以在本地处理。  

## <a name="delegable-data-sources"></a>可委托的数据源
请参阅[委派列表](delegation-list.md)以获取完整的列表，了解哪些数据源支持委派，以及支持到何种程度。

我们会持续为现有的数据源增加委派支持，并且会增加更多的数据源。

导入的 Excel 工作簿（使用“向应用添加静态数据”数据源）、集合以及存储在上下文变量中的表不需要委派。 所有此类数据都已在内存中，可以应用完整的 PowerApps 语言。

## <a name="delegable-functions"></a>委派函数
下一步是仅使用那些可以委派的公式。 下面提供的是可以委派的公式元素。  但是，数据源各不相同，并非所有数据源都支持所有这些元素。 请查看具体公式中的蓝点建议。

这些列表会随时间而变化。 我们将努力为更多具有委派功能的函数和运算符提供支持。

### <a name="filter-functions"></a>Filter 函数
**[Filter](functions/function-filter-lookup.md)**、**[Search](functions/function-filter-lookup.md)** 和 **[LookUp](functions/function-filter-lookup.md)** 可以委派。  

在 **Filter** 和 **LookUp** 函数中，可以对表的列使用以下项来选择相应的记录：

* **[And](functions/function-logicals.md)**（包括 **[&&](functions/operators.md)**）、**[Or](functions/function-logicals.md)**（包括 **[||](functions/operators.md)**）、**[Not](functions/function-logicals.md)**（包括 **[!](functions/operators.md)**）
* **[In](functions/operators.md)**
* **[=](functions/operators.md)**、**[<>](functions/operators.md)**、**[>=](functions/operators.md)**、**[<=](functions/operators.md)**、**[>](functions/operators.md)**、**[<](functions/operators.md)**
* **[+](functions/operators.md)**、**[-](functions/operators.md)**
* **[TrimEnds](functions/function-trim.md)**
* **[IsBlank](functions/function-isblank-isempty.md)**
* **[StartsWith](functions/function-startswith.md)**
* 所有记录中均相同的常量值，如控件属性和[全局变量和上下文变量](working-with-variables.md)。

如果公式的某些部分对所有记录的求值结果都是一个常量值，则也可使用这些部分。  例如，**Left( Language(), 2 )** 不依赖于记录的任何列，因此所有记录都会返回同一值。  它实际上是一个常量。  使用上下文变量、集合和信号可能不会获得常量，因此会妨碍 **Filter** 和 **LookUp** 委派。  

上面的列表缺少的一些重要项目：

* **[If](functions/function-if.md)**
* **[*](functions/operators.md)**、**[/](functions/operators.md)**、**[Mod](functions/function-mod.md)**
* **[Concatenate](functions/function-concatenate.md)**（包括 **[&](functions/operators.md)**）
* **[ExactIn](functions/operators.md)**
* 字符串操作函数：**[Lower](functions/function-lower-upper-proper.md)**、**[Upper](functions/function-lower-upper-proper.md)**、**[Left](functions/function-left-mid-right.md)**、**[Mid](functions/function-left-mid-right.md)**、**[Len](functions/function-left-mid-right.md)**...
* 信号：**[Location](functions/signals.md)**、**[Acceleration](functions/signals.md)**、**[Compass](functions/signals.md)**...
* 可变函数：**[Now](functions/function-now-today-istoday.md)**、**[Today](functions/function-now-today-istoday.md)**、**[Rand](functions/function-rand.md)**...
* [集合](working-with-variables.md)

### <a name="sorting-functions"></a>排序函数
**[Sort](functions/function-sort.md)** 和 **[SortByColumns](functions/function-sort.md)** 可以委派。  

在 **Sort** 中，公式只能是单个列的名称，不能包括其他运算符或函数。

### <a name="aggregate-functions"></a>聚合函数
可以委派 [Sum](functions/function-aggregates.md)、[Average](functions/function-aggregates.md)、[Min](functions/function-aggregates.md) 和 [Max](functions/function-aggregates.md)。  目前仅有限数量的数据源支持此委派，请查看[委派列表](delegation-list.md)了解更多详细信息。

无法委派 [CountRows](functions/function-table-counts.md)、[CountA](functions/function-table-counts.md) 和 [Count](functions/function-table-counts.md) 等计数函数。

无法委派 [StdevP](functions/function-aggregates.md) 和 [VarP](functions/function-aggregates.md) 等其他聚合函数。

### <a name="other-functions"></a>其他函数
所有其他函数都不支持委派，包括以下重要函数：

* 表整理：**[AddColumns](functions/function-table-shaping.md)**、**[DropColumns](functions/function-table-shaping.md)**、**[ShowColumns](functions/function-table-shaping.md)**...
* **[First](functions/function-first-last.md)**、**[FirstN](functions/function-first-last.md)**、**[Last](functions/function-first-last.md)**、**[LastN](functions/function-first-last.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Collect](functions/function-clear-collect-clearcollect.md)**、**[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)**、**[RemoveIf](functions/function-remove-removeif.md)**、**[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)**、**[Ungroup](functions/function-groupby.md)**

常见模式是使用 **AddColumns** 和 **LookUp** 将一个表中的信息合并到另一个表中，用数据库术语来说，通常就是指“联接”。  例如：

**AddColumns( Products, "Supplier Name", LookUp( Suppliers, Suppliers.ID = Product.SupplierID ).Name )**

即使 **Products** 和 **Suppliers** 是可委派的数据源且 **LookUp** 是可委派的函数，**AddColumns** 函数也不可委派。  整个公式的结果将仅限于 **Products** 数据源的第一部分。  

由于 **LookUp** 及其数据源可以委派，因此可能会在数据源的任何位置找到 **Suppliers** 的匹配项，即使该数据源很大。  可能的缺点在于，对于 **Products** 中第一部分的每个记录，**LookUp** 都会向数据源发出单独的调用，导致网络上出现大量的零碎信息。  如果 **Suppliers** 够小且不会经常改变，则可在应用启动时通过调用 **Collect** 将数据源缓存在应用中（在打开的屏幕上使用 [**OnVisible**](controls/control-screen.md)），然后改为对其执行 **LookUp**。  

## <a name="non-delegable-limits"></a>不可委派限制
将在本地处理不可委派的公式。  这样就可以使用整套 PowerApps 公式语言。  但是也有代价：所有数据都必须先转到设备上，这可能需要通过网络检索大量的数据。  这可能需要一段时间，让人以为应用很慢或者可能已挂起。

为了避免这种情况，PowerApps 对能够在本地处理的数据量施加了一个限制：500 条记录。  我们选择此数字是为了让你仍然能够对小型数据集进行完整的访问，同时让你虽然只能看到部分结果，也能练习对大型数据集的使用。

显然，使用此工具时必须小心，因为这可能会让用户感到困惑。  例如，你有一个 **Filter** 函数，其选择公式不能委派，你需要对一个记录数为 1 百万的数据源应用该函数。  由于筛选在本地进行，因此只会扫描这 1 百万记录中的前 500 个记录。  如果所需记录是第 501 或第 500,001 个记录，则 **Filter** 不会考虑或返回该记录。

另一可能会造成混淆的情形是使用聚合函数。  对上述包含百万记录的数据源的一个列运行 **Average** 函数。  由于 **Average** 尚无法进行委派，因此只会对前 500 个记录进行平均。  必须小心这种情况，否则你会将应用用户基于部分数据得出的答案误认为是基于完整数据得出的答案。

## <a name="blue-dot-suggestions"></a>蓝点建议
为了方便用户了解什么可以委派，什么不可以委派，特此根据创作体验提出了蓝点建议，这些建议针对的是包含不可委派内容的公式。

蓝点仅显示在针对可委派数据源进行运算的公式上。  如果没有看到蓝点，但你认为公式未进行适当的委派，请对照上面的<a href="#delegable-data-sources">可委派数据源</a>列表检查数据源的类型。

## <a name="examples"></a>示例
在此示例中，我们将使用一个 SQL Server 表，其中包含产品，具体说来就是水果，其名称为 **[dbo].[Products]**。  在“新建”屏幕上，PowerApps 可以创建一个基本的三屏幕应用，该应用连接到以下数据源：

![三屏幕应用](media/delegation-overview/products-afd.png)

请注意库的 **Items** 属性的公式。  该公式使用 **SortByColumns** 和 **Search** 函数，二者均可委派。

让我们在搜索文本输入控件中键入“Apple”。  如果仔细观察，我们就会发现，在新搜索中处理新条目时，屏幕顶部会短暂地出现一串移动的点。  这串移动的点表示我们正在与 SQL Server 通信：

![搜索文本输入控件](media/delegation-overview/products-apple.png)

由于这都是可以委派的，因此即使 **[dbo].[Products]** 表包含数百万记录，我们也仍然可以全部找到它们，当用户滚动浏览结果时在库中对这些记录分页。

你会注意到，我们看到的匹配项包含“Apple”和“Pineapple”。  **Search** 函数会在文本列的任何位置查找搜索词。  如果我们只想在水果名称的开头查找搜索词，  则可使用另一委派函数：**Filter**，该函数的搜索词更复杂（为简便起见，我们将删除 **SortByColumns** 调用）：

![删除 SortByColumns 调用](media/delegation-overview/products-apple-bluedot.png)

看起来发挥作用了，仅“Apples”显示，“Pineapple”没有显示。  但是，在库旁边显示了一个蓝点，在部分公式下标有蓝色的波浪线。  甚至在屏幕缩略图中也显示了一个蓝点。  如果我们将鼠标悬停在库旁边的蓝点上方，则会显示以下消息：

![将鼠标悬停在蓝点之上](media/delegation-overview/products-apple-bluepopup.png)

虽然我们使用的 **Filter** 是可委派的函数，使用的 SQL Server 是可委派的数据源，但在 **Filter** 中使用的公式是不可委派的。  **Mid** 和 **Len** 不能委派给任何数据源。

但它确起作用了，不是吗？  嗯，在某种程度上可以这么说。  这就是为何只显示蓝点而不显示黄色危险图标和红色波浪线（表示错误）的原因。  如果 **[dbo].[Products]** 表包含的记录不到 500 条，则没错，此方法完全可以使用。   所有记录都会转到设备，并在本地应用 **Filter**。  

但如果该表包含的记录超过 500 条，则只会在库中显示表的头 500 条记录中以“Apple”开头的水果。  如果“Apple, Fuji”作为名称出现在第 501 或 500,001 条记录中，就会找不到它。
