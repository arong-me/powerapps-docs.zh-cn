---
title: Trim 和 TrimEnds 函数 | Microsoft 文档
description: PowerApps 中 Trim 和 TrimEnds 函数的参考信息，包括语法和示例
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 09/09/2016
ms.author: gregli
ms.openlocfilehash: 38aa25c46bf8b29c413ca9c3df92f9528bfa97d5
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31831112"
---
# <a name="trim-and-trimends-functions-in-powerapps"></a>PowerApps 中的 Trim 和 TrimEnds 函数
从文本字符串中删除多余空格。

## <a name="description"></a>描述
**Trim** 函数可删除文本字符串中的所有空格，单词之间的单个空格除外。  

**TrimEnds** 函数可删除文本字符串开头和结尾的所有空格，但保留单词之间的空格。

如果指定单个文本字符串，则任一函数的返回值均为删除了所有多余空格的字符串。 如果指定包含字符串的单列[表格](../working-with-tables.md)，则返回值为修整的字符串的单列表格。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

通过修剪单词之间的空格，**Trim** 与 Microsoft Excel 中相同名称的函数一致。 但是，**TrimEnds** 与仅修剪每个字符串开头和结尾空格的编程工具一致。

## <a name="syntax"></a>语法
**Trim**( *String* )<br>**TrimEnds**( *String* )

* *String* - 必需。 要从中删除空格的文本字符串。

**Trim**( *SingleColumnTable* )<br>**TrimEnds**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要从中删除空格的字符串的单列列表。

## <a name="example"></a>示例
| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Trim(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |删除字符串开头和结尾的所有空格，并删除字符串内的多余空格。 |“Hello World” |
| **TrimEnds(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |删除字符串开头和结尾的所有空格。 |“Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World” |

以下示例使用名为 **Spaces** 的单列集合，其中包含下列字符串：

![](media/function-trim/input-strings.png)

若要创建此集合，请将**[按钮](../controls/control-button.md)** 控件的 **OnSelect** 属性设置为以下公式，打开“预览”模式，然后单击或点击按钮：
<br>**ClearCollect( Spaces, [ "&nbsp;&nbsp;&nbsp;Jane&nbsp;&nbsp;&nbsp;Doe&nbsp;&nbsp;&nbsp;", "&nbsp;&nbsp;&nbsp;&nbsp;Jack&nbsp;&nbsp;&nbsp;and&nbsp;&nbsp;&nbsp;Jill", "Already&nbsp;trimmed", "&nbsp;&nbsp;&nbsp;Venus,&nbsp;&nbsp;&nbsp;Earth,&nbsp;&nbsp;&nbsp;Mars&nbsp;&nbsp;", "Oil&nbsp;and&nbsp;Water&nbsp;&nbsp;&nbsp;" ] )**

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Trim(&nbsp;Spaces&nbsp;)** |修剪 **Spaces** 集合中每个字符串开头和结尾的所有空格，以及该集合中每个字符串内的多余空格。 |<style> img { max-width: none } </style> ![](media/function-trim/output-trim.png) |
| **TrimEnds(&nbsp;Spaces&nbsp;)** |修剪 **Spaces** 集合中每个字符串开头和结尾的所有空格。 |<style> img { max-width: none } </style> ![](media/function-trim/output-trimends.png) |

> [!NOTE]
> 如果通过单击或点击“文件”菜单上的“集合”来显示集合，则不会出现多余空格。 若要验证字符串长度，请使用 **[Len](function-len.md)** 函数。

