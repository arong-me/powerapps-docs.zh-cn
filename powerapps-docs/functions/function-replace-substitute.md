---
title: "Replace 和 Substitute 函数 | Microsoft 文档"
description: "PowerApps 中 Replace 和 Substitute 函数的引用信息（包括语法）"
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
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: fe8f1e1cc8e54c3abf4b44bbfe46d9f96a7adfe7
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>PowerApps 中的 Replace 和 Substitute 函数
将文本字符串的一部分替换为其他字符串。

## <a name="description"></a>说明
**Replace** 函数按起始位置和长度标识要替换的文本。  

**Substitute** 函数通过匹配字符串标识要替换的文本。  如果找到多个匹配项，可以控制要替换哪一个。

如果传递单个字符串，则返回值为修改后的字符串。  如果传递包含字符串的单列[表](../working-with-tables.md)，则返回值为修改后字符串的单列表。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

## <a name="syntax"></a>语法
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String* - 必需。 要运算的字符串。
* *StartingPosition* - 必需。  开始替换的字符位置。 *String* 的第一个字符位于位置 1。
* *NumberOfCharacters* - 必需。  *String* 中要替换的字符数。
* *NewString* - 必需。  替换字符串。 此参数中的字符数可能与 *NumberOfCharacters* 参数中的字符数不同。

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String* - 必需。 要运算的字符串。
* *OldString* - 必需。  要替换的字符串。
* *NewString* - 必需。  替换字符串。 *OldString* 和 *NewString* 可以有不同长度。
* *InstanceNumber* - 可选。 默认情况下将替换 *OldString* 的第一个实例。 如果 *String* 包含多个实例，则可以指定要替换哪个实例。

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *StartingPosition* - 必需。  开始替换的字符位置。  表中每个字符串的第一个字符位于位置 1。
* *NumberOfCharacters* - 必需。  每个字符串中要替换的字符数。
* *NewString* - 必需。  替换字符串。 此参数中的字符数可能与 *NumberOfCharacters* 参数中的字符数不同。

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 必需。 要运算的字符串的单列表。
* *OldString* - 必需。  要替换的字符串。
* *NewString* - 必需。  替换字符串。 *OldString* 和 *NewString* 可以有不同长度。
* *InstanceNumber* - 可选。 默认情况下将替换 *OldString* 的第一个实例。 如果表包含多个实例，则可以指定要替换哪个实例。

