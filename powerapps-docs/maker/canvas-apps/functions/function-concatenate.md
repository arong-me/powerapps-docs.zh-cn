---
title: Concat 和 Concatenate 函数 | Microsoft 文档
description: PowerApps 中 Concat 和 Concatenate 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 08/28/2017
ms.author: gregli
ms.openlocfilehash: a735cb17b0e70afcae439044491a603aa50ceae7
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826145"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps 中的 Concat 和 Concatenate 函数
将[表](../working-with-tables.md)中的文本和字符串连成单个字符串。

## <a name="description"></a>描述
**Concat** 函数可将应用于表中所有[记录](../working-with-tables.md#records)的公式的结果串联起来，从而产生单个字符串。 使用这个函数可汇总表的字符串，就像 **[Sum](function-aggregates.md)** 函数可以汇总数字一样。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[Split](function-split.md) 函数可用于将字符串拆分成子字符串表。

**Concatenate** 函数可将混合的单独字符串和单列表中的字符串连接起来。 这个函用于单独字符串时等同于 **&**[ 运算符](operators.md)。 你可以使用包含 **[ShowColumns](function-table-shaping.md)** 函数的公式，将包含多列的表创建一个单列表。

## <a name="syntax"></a>语法
**Concat**( *Table*, *Formula* )

* *Table* - 必需。  要运算的表。
* *Formula* - 必需。  要对表中的记录应用的公式。

**Concatenate**( *String1* [, *String2*, ...] )

* *String(s)* - 必需。  单独字符串或单列表中字符串的混合形式。

## <a name="examples"></a>示例
#### <a name="concat"></a>Concat
1. 添加“**[按钮](../controls/control-button.md)**”控件，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：
   
    **Collect(Products, {String:"Violin", Wind:"Trombone", Percussion:"Bongos"}, {String:"Cello", Wind:"Trumpet", Percussion:"Tambourine"})**
2. 按 F5，单击按钮，然后按 Esc 键返回设计工作区。
3. 添加一个“[标签](../controls/control-text-box.md)”控件，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式：
   
    **Concat(Products, String & " ")**
   
    这个标签会显示 **Violin Cello**。

#### <a name="concatenate"></a>Concatenate
1. 添加一个“[文本输入](../controls/control-text-input.md)”控件，然后将它命名为“AuthorName”。
2. 添加一个“[标签](../controls/control-text-box.md)”控件，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式：<br>
   **Concatenate("By ", AuthorName.Text)**
3. 在 **AuthorName** 中输入你的姓名。
   
    这个标签会显示 **By**，后跟你的姓名。

如果有一个 **Employees** 表，其中包含 **FirstName** 列和 **LastName** 列，以下公式会将这两列中每一行的数据串联起来。
<br>**Concatenate(Employees.FirstName, " ", Employees.LastName)**

