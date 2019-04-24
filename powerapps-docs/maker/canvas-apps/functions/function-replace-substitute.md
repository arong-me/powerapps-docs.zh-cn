---
title: Replace 和 Substitute 函数 | Microsoft 文档
description: PowerApps 中 Replace 和 Substitute 函数的引用信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fca1953402c87ca13bc3560b827cde03a47a8e92
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551597"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>PowerApps 中的 Replace 和 Substitute 函数
将文本字符串的一部分替换为其他字符串。

## <a name="description"></a>描述
**Replace** 函数按起始位置和长度标识要替换的文本。  

**Substitute** 函数通过匹配字符串标识要替换的文本。 如果找到多个匹配项，则可以将所有这些或指定要替换的一个。

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
* *InstanceNumber* - 可选。 使用此参数指定哪个实例*OldString*替换; 如果*字符串*包含多个实例。 如果未指定此参数，将替换所有实例。

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *StartingPosition* - 必需。 开始替换的字符位置。  表中每个字符串的第一个字符位于位置 1。
* *NumberOfCharacters* - 必需。 每个字符串中要替换的字符数。
* *NewString* - 必需。  替换字符串。 此参数中的字符数可能与 *NumberOfCharacters* 参数中的字符数不同。

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *OldString* - 必需。  要替换的字符串。
* *NewString* - 必需。  替换字符串。 *OldString* 和 *NewString* 可以有不同长度。
* *InstanceNumber* - 可选。 使用此参数指定哪个实例*OldString*替换; 如果*字符串*包含多个实例。 如果未指定此参数，将替换所有实例。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Replace( "abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*" )** | 在"abcdefghijk"中的五个字符替换为单个"*"字符，第六个字符 ("f") 开头。 | "abcde*k" |
| **Replace(&nbsp;"2019",&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | 替换"2019"与"20"的最后两个字符。 | "2020" |
| **Replace(&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | 替换单个"_"字符"123456"的前三个字符。 | "_456" | 
| **Substitute(&nbsp;"Sales&nbsp;Data",&nbsp;"Sales",&nbsp;"Cost"&nbsp;)** | 替换字符串为"Sales"的"成本"。 | "成本数据" | 
| **Substitute( "Quarter&nbsp;1,&nbsp;2018", "1", "2", 1 )** | 将替换仅用"2""1"的第一个实例，因为第四个参数 (*InstanceNumber*) 提供了 1。 |  "第 2 季度，2018年" |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2", 3 )** | 替换只有"1"与"2"的第三个实例，因为第四个参数 (*InstanceNumber*) 提供 3。 | "第 1 季度，2012年" |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2" )** | 替换为"1"与"2"的所有实例，因为第四个参数 (*InstanceNumber*) 未提供。 | "第 2 季度，2022年" |
| **Replace(<br>[&nbsp;"Quarter&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;2,&nbsp;2011",<br>"Quarter&nbsp;4,&nbsp;2019" ],<br>9,  1, "3" )** | 将替换"3"的单列的表的每个记录中的第九个字符。 | [&nbsp;"Quarter&nbsp;3,&nbsp;2018",<br>"每个季度&nbsp;3，&nbsp;2011年"，<br>"每个季度&nbsp;3，&nbsp;2019年"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3", 1 )** | 因为第四个参数 (*InstanceNumber*) 值为 1，将替换为"1"中的，仅第一个实例中提供"3"的单列的表的每个记录。 | [&nbsp;"Qtr&nbsp;3,&nbsp;2018",<br>"每个季度&nbsp;3，&nbsp;2011年"，<br>"Q3,&nbsp;2019"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3" )** | 因为第四个参数 (*InstanceNumber*) 未提供，将替换为"1"与"3"的单列的表的每个记录中的所有实例。 | [&nbsp;"Qtr&nbsp;3,&nbsp;2038",<br>"Quarter&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 


