---
title: Left、Mid 和 Right 函数 | Microsoft 文档
description: Power Apps 中 Left、Mid 和 Right 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2a8f89dff09d34d7492f325f54f73c4c736adc24
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145411"
---
# <a name="left-mid-and-right-functions-in-power-apps"></a>Power Apps 中的 Left、Mid 和 Right 函数
提取文本字符串的左侧、中间或右侧部分。

## <a name="description"></a>说明
**Left**、**Mid** 和 **Right** 函数返回字符串的一部分。

* **Left** 返回字符串的起始字符。
* **Mid** 返回字符串的中间字符。
* **Right** 返回字符串的结尾字符。

如果指定单个字符串作为参数，则函数将返回所请求的字符串部分。 如果指定包含字符串的单列[表](../working-with-tables.md)，则函数将返回所请求的这些字符串的单列表部分。 如果指定一个多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

如果起始位置为负或超过字符串末尾，**Mid** 将返回空白。  可使用 **[Len](function-len.md)** 函数检查字符串的长度。 如果所请求的字符数超过字符串包含的字符数，函数将尽可能多地返回字符。

## <a name="syntax"></a>语法
**Left**( *String*, *NumberOfCharacters* )<br>**Mid**（ *String*， *StartingPosition* [， *NumberOfCharacters* ]）<br>**Right**( *String*, *NumberOfCharacters* )

* *String* - 必需。 到要从中提取结果的字符串。
* *StartingPosition* - 必需（仅限 **Mid**  起始位置。  字符串的第一个字符是位置 1。
* *NumberOfCharacters* -必需（仅**向左**和**向右**）。  要返回的字符数。  如果**Mid**函数省略此函数，则该函数将返回从起始位置到字符串末尾的部分。

**Left**( *SingleColumnTable*, *NumberOfCharacters* )<br>**Mid**（ *SingleColumnTable*， *StartingPosition* [， *NumberOfCharacters* ]）<br>**Right**( *SingleColumnTable*, *NumberOfCharacters* )

* *SingleColumnTable* - 必需。 要从中提取结果的字符串的单列表。
* *StartingPosition* - 必需（仅限 **Mid**  起始位置。  字符串的第一个字符是位置 1。
* *NumberOfCharacters* -必需（仅**向左**和**向右**）。  要返回的字符数。  如果**Mid**函数省略此函数，则该函数将返回从起始位置到字符串末尾的部分。

## <a name="examples"></a>示例
### <a name="single-string"></a>单个字符串
此部分中的示例使用文本输入控件作为[数据源](../working-with-data-sources.md)。 该控件名为 **Author**，包含字符串“E. E. Cummings”。

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Left( Author.Text, 5 )** |从字符串开头处提取最多五个字符。 |“E. E.” |
| **Mid( Author.Text, 7, 4 )** |从字符串的第七个字符开始，提取最多四个字符。 |“Cumm” |
| **Mid （Author，7）** |从字符串中提取所有字符，从第七个字符开始。 |"Cummings" |
| **Right( Author.Text, 5 )** |从字符串的末尾处提取最多五个字符。 |“mings” |

### <a name="single-column-table"></a>单列表
本部分中的每个示例都将从此数据源的**Address** [列](../working-with-tables.md#columns)中提取名为 "**人员**" 的字符串，并返回包含结果的单列表：

![](media/function-left-mid-right/people-table.png)

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 8 )** |提取每个字符串的前八个字符。 |<style>img {最大宽度：无}</style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 5, 7 )** |提取每个字符串的中间七个字符，从第五个字符开始提取。 |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 7 )** |提取每个字符串的最后七个字符。 |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>分步示例
1. 导入或创建一个名为[清单](../working-with-data-sources.md#collections)的**集合**，并在库中显示它，如[在库中显示图像和文本 ](../show-images-text-gallery-sort-filter.md)所述的第一个过程。
2. 将库中下层标签的 **[Text](../controls/properties-core.md)** 属性设置为以下函数：
   
    **Right(ThisItem.ProductName, 3)**
   
    该标签显示每个产品名称的最后三个字符。

