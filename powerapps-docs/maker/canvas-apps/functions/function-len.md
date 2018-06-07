---
title: Len 函数 | Microsoft 文档
description: PowerApps 中 Len 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 9b35f8c935fa0cdb7c27db5eaf8b89eae242efc4
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31827956"
---
# <a name="len-function-in-powerapps"></a>PowerApps 中的 Len 函数
返回文本字符串的长度。

## <a name="description"></a>描述
如果将单个字符串指定为参数，则返回值是数字形式的长度。  如果指定一个包含字符串的单列[表](../working-with-tables.md)，则返回值是一个单列表，其中包含每个字符串的长度。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

如果指定[空](function-isblank-isempty.md)字符串，则 **Len** 返回 0。

## <a name="syntax"></a>语法
**Len**( *String* )

* *String* - 必需。 要度量的字符串。

**Len**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要计算字符串长度的单列表。

## <a name="examples"></a>示例
### <a name="single-string"></a>单个字符串
对于本部分中的示例，[数据源](../working-with-data-sources.md)是名为“Author”的文本输入控件，其中包含字符串“E. E. Cummings”。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Len( Author.Text )** |计算 **Author** 控件中字符串的长度。 |14 |
| **Len( "" )** |计算空字符串的长度。 |0 |

### <a name="single-column-table"></a>单列表
对于本节中的第一个示例，数据源名为 **People**，并且包含以下数据：

![](media/function-len/people-table.png)

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Len( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |在 **People** 表的 **Address** [列](../working-with-tables.md#columns) 中：<br><ul><li>计算每个字符串的长度。</li><li>返回一个单列表，其中包含每个字符串的长度。</li> |<style> img { max-width: none } </style> ![](media/function-len/people-table-len.png) |
| **Len( [ "Hello", "to the", "World", "" ] )** |在内联表的 **[Value](function-value.md)** 列中：<br><ul><li>计算每个字符串的长度。</li><li>返回一个单列表，其中包含每个字符串的长度。</li> |![](media/function-len/people-table-len-inline.png) |

