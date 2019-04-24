---
title: DataSourceInfo 函数 | Microsoft 文档
description: PowerApps 中 DataSourceInfo 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: d856ccd086a919e206175c25eee19f435325fb8c
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551277"
---
# <a name="datasourceinfo-function-in-powerapps"></a>PowerApps 中的 DataSourceInfo 函数
提供[数据源](../working-with-data-sources.md)的相关信息。

## <a name="overview"></a>概述
数据源可以提供丰富的信息，用于优化用户体验。

可以使用[列](../working-with-tables.md#columns)-级别信息验证用户输入并在使用 **[Patch](function-patch.md)** 函数前向用户提供即时反馈。 **[Validate](function-validate.md)** 函数使用同一信息。

例如，可在数据源级别使用信息，以针对无权编辑或创建[记录](../working-with-tables.md#records)的用户禁用或隐藏“编辑”和“新建”按钮。

数据源中提供的信息量可能会不同，包括不提供任何信息。  [Collections](../working-with-data-sources.md#collections) 不提供信息。 如果一条信息也不提供，则使用默认值，或返回空白。

## <a name="description"></a>描述
### <a name="column-information"></a>列信息
可以使用 **DataSourceInfo** 获取数据源的特定列的相关信息：  

| 信息自变量 | 结果类型 | 描述 |
| --- | --- | --- |
| **DataSourceInfo.DisplayName** |String |列的显示名称。 如果未定义显示名称，将返回列名称。 |
| **DataSourceInfo.MaxLength** |Number |列所能容纳的最大字符数。 仅适用于包含字符串的列。 如果未设置最大值，则返回空白。 |
| **DataSourceInfo.MaxValue** |Number |列所能容纳的最大数值。 仅适用于包含数字的列。 如果未设置最大值，则返回空白。 |
| **DataSourceInfo.MinValue** |Number |列所能容纳的最小数值。 仅适用于包含数字的列。 如果未设置最小值，则返回空白。 |
| **DataSourceInfo.Required** |Boolean |此列是否需要值？ 如果数据源未对此进行设置，则返回 **false**。 |

第三个自变量是字符串形式的列名称。  例如，集合**人员**中的“手机”列将传递为“Phone”（含双引号）。

### <a name="data-source-information"></a>数据源信息
还可以使用 **DataSourceInfo** 获取整体数据源的信息：  

| 信息自变量 | 结果类型 | 描述 |
| --- | --- | --- |
| **DataSourceInfo.AllowedValues** |Boolean |可以向用户授予对此数据源的哪些类型权限？ 如果数据源未设置，则返回 *空白* 值。 |
| **DataSourceInfo.CreatePermission** |Boolean |当前用户是否有权在此数据源中创建记录？ 如果数据源未设置，将返回 **true**。 |
| **DataSourceInfo.DeletePermission** |Boolean |当前用户是否有权在此数据源中删除记录？ 如果数据源未设置，将返回 **true**。 |
| **DataSourceInfo.EditPermission** |Boolean |当前用户是否有权在此数据源中编辑记录？ 如果数据源未设置，将返回 **true**。 |
| **DataSourceInfo.ReadPermission** |Boolean |当前用户是否有权在此数据源中读取记录？ 如果数据源未设置，将返回 **true**。 |

## <a name="syntax"></a>语法
**DataSourceInfo**( *DataSource*, *Information*, *ColumnName* )

* *DataSource* – 必需。 要使用的数据源。
* *Information* – 必需。 要检索的信息类型。
* *ColumnName* – 可选。 对于列级信息，为字符串形式的列名称。 例如，“手机”列将传递为“Phone”（含双引号）。 对于数据源级别的信息，不能使用 ColumnName 自变量。
  
    > [!NOTE]
  > 对于列名称带空格的 SharePoint 和 Excel 数据源，请将每个空格指定为“\_x0020\_”。 例如，将“Column Name”指定为“Column_x0020_Name”。

## <a name="examples"></a>示例
本部分中的示例使用以下名为 **IceCream** 的数据源：

![](media/function-datasourceinfo/icecream.png)

数据源还提供以下信息：

* “数量”的显示名称是“现有数量”。
* “风格”的最大长度是 30 个字符。
* “风格”列必须包含值。 “数量”列不是必需的。
* 最小**数量**为 0。
* 最大**数量**为 100。
* 当前用户可读取和编辑 **IceCream** 数据源的记录，但无法创建或删除记录。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DisplayName,&nbsp;"Quantity"&nbsp;)** |返回 **IceCream** 数据源的“数量”列的显示名称。 |“现有数量” |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxLength,&nbsp;"Flavor"&nbsp;)** |返回 **IceCream** 数据源的“风格”列的字符串的最大长度。 |30 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Flavor"&nbsp;)** |**IceCream** 数据源的“风格”列是否为必需？ |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Quantity"&nbsp;)** |**IceCream** 数据源的“数量”列是否为必需？ |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxValue,&nbsp;"Quantity"&nbsp;)** |返回 **IceCream** 数据源的“数量”列的最大值。 |100 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MinValue,&nbsp;"Quantity"&nbsp;)** |返回 **IceCream** 数据源的“数量”列的最小值。 |0 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.ReadPermission)** |当前用户是否可以在 **IceCream** 数据源中读取记录？ |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.EditPermission)** |当前用户是否可以在 **IceCream** 数据源中编辑记录？ |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.CreatePermission)** |当前用户是否可以在 **IceCream** 数据源中创建记录？ |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DeletePermission)** |当前用户是否可以在 **IceCream** 数据源中删除记录？ |**false** |

