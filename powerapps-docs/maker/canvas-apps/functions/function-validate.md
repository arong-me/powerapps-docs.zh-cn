---
title: Validate 函数 | Microsoft 文档
description: PowerApps 中 Validate 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: 2b3d91a6da0e17ded435aec74a88ea1bbdd4fac1
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31827726"
---
# <a name="validate-function-in-powerapps"></a>PowerApps 中的 Validate 函数
**Validate** 函数检查单个[列](../working-with-tables.md#columns)或整条[记录](../working-with-tables.md#records)的值对[数据源](../working-with-data-sources.md)是否有效。  

## <a name="description"></a>描述
在用户提交数据更改之前，你可以针对该提交的有效性提供即时反馈，改进用户体验。

对于何种要素构成记录中的有效值，数据源可以提供相关信息。 该信息可能包括许多约束，例如以下示例：

* 列是否需要值
* 文本字符串可以有多长
* 一个数字可以有多大和多小
* 一个日期可以有多早和多迟

**Validate** 函数根据该信息来确定某个值是否有效，并在无效的情况下返回相应的错误消息。 可以通过 **[DataSourceInfo](function-datasourceinfo.md)** 函数查看 **Validate** 所使用的相同信息。

数据源中提供的验证信息量可能不同，甚至可能不提供任何信息。 **Validate** 只能根据该信息验证值。 即使 **Validate** 没有发现问题，仍然可能无法应用数据更改。 可以通过 **[Errors](function-errors.md)** 函数获取有关失败的信息。

如果 **Validate** 发现问题，该函数会返回错误消息，方便你将其显示给应用用户。 如果所有值都有效，**Validate** 返回[空白](function-isblank-isempty.md)。 使用没有验证信息的[集合](../working-with-data-sources.md#collections)时，值始终是有效的。

## <a name="syntax"></a>语法
**Validate**( *DataSource*, *Column*, *Value* )

* *DataSource* – 必需。 要通过其进行验证的数据源。
* *Column* - 必需。 要验证的列。
* *Value* - 必需。 要验证的所选列的值。

**Validate**( *DataSource*, *OriginalRecord*, *Updates* )

* *DataSource* – 必需。 要通过其进行验证的数据源。
* *OriginalRecord* - 必需。  要验证其更新的记录。
* *Updates* - 必需。  将应用于原始记录的更改。

## <a name="examples"></a>示例
就这些示例来说，**Scores** 数据源的 **Percentage** 列中的值必须为 0 到 100（含）之间。 如果数据通过验证，该函数将返回空白。 否则，该函数返回一条错误消息。

### <a name="validate-with-a-single-column"></a>验证单个列
| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Validate( Scores, Percentage, 10 )** |对于 **Scores** 数据源的 **Percentage** 列，检查 **10** 是否为有效值。 |空白 |
| **Validate( Scores, Percentage, 120 )** |对于 **Scores** 数据源的 **Percentage** 列，检查 **120** 是否为有效值。 |“值必须为 0 到 100 之间。” |

### <a name="validate-with-a-complete-record"></a>验证完整记录
| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Validate( Scores, EditRecord, Gallery.Updates )** |对于 **Scores** 数据源的 **Percentage** 列，检查 **10** 是否为有效值。 |空白 |
| **Validate( Scores, EditRecord, Gallery.Updates )** |对于 **Scores** 数据源的 **Percentage** 列，检查 **120** 是否为有效值。 |“值必须为 0 到 100 之间。” |

