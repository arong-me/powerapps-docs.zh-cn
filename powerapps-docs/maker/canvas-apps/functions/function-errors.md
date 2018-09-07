---
title: Errors 函数 | Microsoft 文档
description: PowerApps 中 Errors 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 886479b4cd2f7e04e9949c99ba05e6219e92b2b3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42859977"
---
# <a name="errors-function-in-powerapps"></a>PowerApps 中的 Errors 函数
提供之前对[数据源](../working-with-data-sources.md)的更改的错误信息。

## <a name="overview"></a>概述
数据源的[记录](../working-with-tables.md#records)发生更改时可能会出现错误。  导致错误的原因有许多，包括网络故障、权限不足和编辑冲突。  

**[Patch](function-patch.md)** 函数和其他数据函数不直接返回错误。 而会返回其运算的结果。 数据函数执行后，可使用 **Errors** 函数获取任何错误的详细信息。  可在公式 **IsEmpty( Errors ( ... ) )** 中使用 **[IsEmpty]** 函数检查是否存在错误。

可使用 **[Validate](function-validate.md)** 和 **[DataSourceInfo](function-datasourceinfo.md)** 函数在错误出现之前避免这些错误。  请参阅[使用数据源](../working-with-data-sources.md)，了解如何处理和避免错误的更多建议。

## <a name="description"></a>描述
**Errors** 函数会返回一个错误的[表](../working-with-tables.md)，其中包含以下[列](../working-with-tables.md#columns)：

* **记录**。  数据源中有错误的记录。  如果在记录的创建过程中发生错误，此列将为*空白*。
* **列**。  导致错误的列（如果该错误可归因于单个列）。 如果没有，此列将为*空白*。
* **消息**。  错误的说明。  可为最终用户显示此错误字符串。  请注意，此消息可能由数据源生成，可能会很长且包含可能对用户没有任何意义的原始列名称。
* **错误**。  可在公式中使用以帮助解决错误的错误代码：

| ErrorKind | 描述 |
| --- | --- |
| ErrorKind.Conflict |对同一个记录进行了其他更改，从而导致更改冲突。  使用 **[Refresh](function-refresh.md)** 函数重新加载记录，尝试再次进行更改。 |
| ErrorKind.ConstraintViolation |违反了一个或多个约束。 |
| ErrorKind.CreatePermission |尝试创建一个记录，但当前用户没有权限创建记录。 |
| ErrorKind.DeletePermission |尝试删除一个记录，但当前用户没有权限删除记录。 |
| ErrorKind.EditPermission |尝试编辑一个记录，但当前用户没有权限编辑记录。 |
| ErrorKind.GeneratedValue |尝试更改数据源自动生成的列。 |
| ErrorKind.MissingRequired |记录中缺少所需列的值。 |
| ErrorKind.None |不存在错误。 |
| ErrorKind.NotFound |尝试编辑或删除一个记录，但找不到该记录。  其他用户可能已更改该记录。 |
| ErrorKind.ReadOnlyValue |尝试更改只读列。 |
| ErrorKind.Sync |数据源报告了错误。  查看“消息”列了解详细信息。 |
| ErrorKind.Unknown |存在未知类型的错误。 |
| ErrorKind.Validation |检测到一个常规的验证问题，不符合其他任一类型。 |

通过向函数提供 *Record* 参数，可针对整个数据源，也可仅针对选定的行返回错误。  

如果无法创建记录，**[Patch](function-patch.md)** 或其他数据函数可能会返回*空白*值。 可以将 *blank* 传递到 **Errors**，它将在这类情况下返回相应的错误信息。  随后对同一数据源使用数据函数将清除此错误信息。

如果没有错误，**Errors** 返回的表将为[空](function-isblank-isempty.md)，且可使用 **[IsEmpty](function-isblank-isempty.md)** 函数进行测试。

## <a name="syntax"></a>语法
**Errors**( *DataSource* [, *Record* ] )

* *DataSource* - 必需。 要为其返回错误的数据源。
* *记录* - 可选。  要为其返回错误的特定记录。 如果未指定此参数，函数将返回整个数据源的错误。

## <a name="examples"></a>示例
### <a name="step-by-step"></a>分步操作
在此示例中，我们将使用 **IceCream** 数据源：

![](media/function-errors/icecream.png)

通过该应用，用户将 Chocolate 记录加载到一个数据输入窗体中，然后将 **Quantity** 更改为 90。  要使用的记录置于[上下文变量](../working-with-variables.md#create-a-context-variable) **EditRecord** 中：

* **UpdateContext( { EditRecord: First( Filter( IceCream, Flavor = "Chocolate" ) ) } )**

若要在数据源中进行此更改，请使用 **[Patch](function-patch.md)** 函数：

* **Patch( IceCream, EditRecord, Gallery.Updates )**

其中 **Gallery.Updates** 计算结果为 **{ Quantity: 90 }**，因为只修改了 **Quantity** 属性。

但就在调用 **[Patch](function-patch.md)** 函数之前，其他人将 Chocolate 的 **Quantity** 修改为 80。  PowerApps 将检测到此情况，且不允许发生更改冲突。  可使用以下公式检查是否存在这种情况：

* **IsEmpty( Errors( IceCream, EditRecord ) )**

它将返回 **false**，因为 **Errors** 函数返回了下表：

| 记录 | 列 | 消息 | 错误 |
| --- | --- | --- | --- |
| { Flavor: "Chocolate", Quantity: 100 } |空白 |“另一个用户已修改你正尝试修改的记录。 请重新加载该记录，然后重试。” |ErrorKind.Conflict |

可在窗体上放置标签，向用户显示此错误。

* 若要显示错误，请将标签的 **[Text](../controls/properties-core.md)** 属性设置为此公式：<br>
  **Label.Text = First(Errors( IceCream, EditRecord )).Message**

还可以在窗体上添加“重新加载”按钮，使用户可高效地解决冲突。

* 若要只在发生冲突时显示该按钮，请将按钮的 **[Visible](../controls/properties-core.md)** 属性设置为此公式：<br>
    “!IsEmpty( Lookup( Errors( IceCream, EditRecord ), Error = ErrorKind.Conflict ) )”
* 若要还原用户选择此按钮时的更改，请将其 **[OnSelect](../controls/properties-core.md)** 属性设置为此公式：<br>
    “ReloadButton.OnSelect = Revert( IceCream, EditRecord )”

