---
title: Replace 和 Substitute 函数 | Microsoft 文档
description: PowerApps 中 Replace 和 Substitute 函数的引用信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff0e016f6ab1ad4f66651ccd3cfa2711f1d85a38
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992372"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>PowerApps 中的 Replace 和 Substitute 函数
将文本字符串的一部分替换为其他字符串。

## <a name="description"></a>说明
**Replace** 函数按起始位置和长度标识要替换的文本。  

**Substitute** 函数通过匹配字符串标识要替换的文本。 如果找到多个匹配项，则可以替换所有匹配项，也可以指定一个替换项。

如果传递单个字符串，则返回值为修改后的字符串。 如果传递包含字符串的单列[表](../working-with-tables.md)，则返回值为修改后字符串的单列表。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

## <a name="syntax"></a>语法
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String* - 必需。 要运算的字符串。
* *StartingPosition* - 必需。 开始替换的字符位置。 *String* 的第一个字符位于位置 1。
* *NumberOfCharacters* - 必需。 *String* 中要替换的字符数。
* *NewString* - 必需。 替换字符串。 此参数中的字符数可能与 *NumberOfCharacters* 参数中的字符数不同。

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String* - 必需。 要运算的字符串。
* *OldString* - 必需。 要替换的字符串。
* *NewString* - 必需。 替换字符串。 *OldString* 和 *NewString* 可以有不同长度。
* *InstanceNumber* - 可选。 如果*字符串*包含多个实例，则使用此参数指定要替换的*OldString*的实例。 如果未指定此参数，则所有实例都将被替换。

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *StartingPosition* - 必需。 开始替换的字符位置。  表中每个字符串的第一个字符位于位置 1。
* *NumberOfCharacters* - 必需。 每个字符串中要替换的字符数。
* *NewString* - 必需。  替换字符串。 此参数中的字符数可能与 *NumberOfCharacters* 参数中的字符数不同。

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *OldString* - 必需。  要替换的字符串。
* *NewString* - 必需。  替换字符串。 *OldString* 和 *NewString* 可以有不同长度。
* *InstanceNumber* - 可选。 如果*字符串*包含多个实例，则使用此参数指定要替换的*OldString*的实例。 如果未指定此参数，则所有实例都将被替换。

## <a name="examples"></a>示例

| 公式 | 说明 | 结果 |
|---------|-------------|--------|
| **Replace （"abcdefghijk"，&nbsp;6，&nbsp;5，&nbsp;"*"）** | 将 "abcdefghijk" 中的五个字符替换为一个 "*" 字符，以第六个字符（"f"）开头。 | "abcde...z * k" |
| **Replace （&nbsp;"2019"，&nbsp;3，&nbsp;2，&nbsp;"20"&nbsp;）** | 用 "20" 替换最后两个字符 "2019"。 | "2020" |
| **Replace （&nbsp;"123456"，&nbsp;1，&nbsp;3，&nbsp;"_"&nbsp;）** | 将 "123456" 的前三个字符替换为单个 "_" 字符。 | "_456" | 
| **替换（&nbsp;"Sales&nbsp;Data"，&nbsp;"Sales"，&nbsp;"Cost"&nbsp;）** | 将字符串 "Cost" 替换为 "Sales"。 | "成本数据" | 
| **替换（"季度&nbsp;1，&nbsp;2018"，"1"，"2"，1）** | 仅用 "2" 替换第一个实例 "1"，因为使用1提供第四个参数（*InstanceNumber*）。 |  "第2季度，2018" |
| **替换（"季度&nbsp;1，&nbsp;2011"，"1"，"2"，3）** | 仅用 "2" 替换第三个实例 "1"，因为使用3提供第四个参数（*InstanceNumber*）。 | "第1季度，2012" |
| **替换（"季度&nbsp;1，&nbsp;2011"，"1"，"2"）** | 将 "1" 的所有实例替换为 "2"，因为未提供第四个参数（*InstanceNumber*）。 | "第2季度，2022" |
| **Replace （<br>[&nbsp;"季度&nbsp;1，&nbsp;2018"，<br>"季度&nbsp;2，&nbsp;2011"，<br>"季度&nbsp;4，&nbsp;2019"]，<br>9，1，"3"）** | 将单列表表中每个记录的第九个字符替换为 "3"。 | [&nbsp;"季度&nbsp;3，&nbsp;2018"，<br>"季度&nbsp;3，&nbsp;2011"，<br>"季度&nbsp;3，&nbsp;2019"&nbsp;] |
| **替换（<br>[&nbsp;"季度&nbsp;1，&nbsp;2018"，<br>"季度&nbsp;1，&nbsp;2011"，<br>"Q1，&nbsp;2019"&nbsp;]，<br>"1"，"3"，1）** | 因为提供的第四个参数（*InstanceNumber*）的值为1，所以仅用 "3" 替换单列表的每个记录中的第一个实例 "1"。 | [&nbsp;"季度&nbsp;3，&nbsp;2018"，<br>"季度&nbsp;3，&nbsp;2011"，<br>"Q3，&nbsp;2019"&nbsp;] |
| **替换（<br>[&nbsp;"季度&nbsp;1，&nbsp;2018"，<br>"季度&nbsp;1，&nbsp;2011"，<br>"Q1，&nbsp;2019"&nbsp;]，<br>"1"，"3"）** | 由于未提供第四个参数（*InstanceNumber*），请用 "3" 替换单列表的每个记录中 "1" 的所有实例。 | [&nbsp;"季度&nbsp;3，&nbsp;2038"，<br>"季度&nbsp;3，&nbsp;2033"，<br>"Q3，&nbsp;2039"&nbsp;] |  
 


