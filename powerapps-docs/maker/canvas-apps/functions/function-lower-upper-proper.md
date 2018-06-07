---
title: Lower、Upper 和 Proper 函数 | Microsoft 文档
description: PowerApps 中 Lower、Upper 和 Proper 函数的引用信息（包括语法和示例）
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
ms.openlocfilehash: e57ea9208f0ea3b7dd9ada7ebd9055a99ddc141c
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31831768"
---
# <a name="lower-upper-and-proper-functions-in-powerapps"></a>PowerApps 中的 Lower、Upper 和 Proper 函数
将文本字符串中的字母转换为全部小写、全部大写或首字母大写。

## <a name="description"></a>描述
**Lower**、**Upper** 和 **Proper** 函数转换字符串中字母的大小写。

* **Lower** 将所有大写字母转换为小写。
* **Upper** 将所有小写字母转换为大写。
* 如果单词的首字母为小写，**Proper** 会将其转换为大写，并将所有其他大写字母转换为小写。

这三个函数都会忽略不是字母的字符。

如果传递单个字符串，则返回值为该字符串的转换后版本。  如果传递包含字符串的单列[表](../working-with-tables.md)，则返回值为转换后字符串的单列表。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

## <a name="syntax"></a>语法
**Lower**( *String* )<br>**Upper**( *String* )<br>**Proper**( *String* )

* *String* - 必需。 要转换的字符串。

**Lower**( *SingleColumnTable* )<br>**Upper**( *SingleColumnTable* )<br>**Proper**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要转换的字符串的单列表。

## <a name="examples"></a>示例
### <a name="single-string"></a>单个字符串
此部分中的示例使用“Author”文本输入控件作为[数据源](../working-with-data-sources.md)。 该控件包含字符串“E. E. CummINGS”。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Lower(&nbsp;Author.Text&nbsp;)** |将字符串中的所有大写字母转换为小写。 |“e. e. cummings” |
| **Upper(&nbsp;Author.Text&nbsp;)** |将字符串中的所有小写字母转换为大写。 |“E. E. CUMMINGS” |
| **Proper(&nbsp;Author.Text&nbsp;)** |如果单词的首字母为小写，则会将其转换为大写，并将所有其他大写字母转换为小写。 |“E. E. Cummings” |

### <a name="single-column-table"></a>单列表
本部分中的示例将转换 **People** 数据源的 **Address** [列](../working-with-tables.md#columns)中的字符串，其包含的数据如下：

![](media/function-lower-upper-proper/people-table.png)

每个公式返回一个单列表，表中包含转换后的字符串。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |将所有小写字母转换为大写。 |<style> img { max-width:none; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |将所有小写字母转换为大写。 |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |将所有单词的小写首字母转换为大写，并将所有其他大写字母转换为小写。 |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>分步示例
1. 添加**[“文本输入”](../controls/control-text-input.md)** 控件，然后将其命名为“Source”。
2. 添加一个标签，然后将其 **[Text](../controls/properties-core.md)** 属性设置为以下函数：<br>**Proper(Source.Text)**
3. 按 F5，然后将 **WE ARE THE BEST!** 键入 **Source** 框中。<br>标签会显示 **We Are The Best!**

