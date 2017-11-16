---
title: "Split 函数 | Microsoft 文档"
description: "PowerApps 中 Split 函数的参考信息（包括语法和示例）"
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
ms.date: 08/28/2017
ms.author: gregli
ms.openlocfilehash: e1953767c40edbe27a232678bdeaab8cebfdea17
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="split-function-in-powerapps"></a>PowerApps 中的 Split 函数
将文本字符串拆分成子字符串表。

## <a name="description"></a>说明
Split 函数将文本字符串拆分成子字符串表。  Split 可用于拆分以逗号分隔的列表、在各日期部分之间使用斜线的日期，并适用于使用定义完善的分隔符的其他情况。  

分隔符字符串用于拆分文本字符串。  分隔符可以是零个、一个或多个字符，整体可以在文本字符串中找到匹配项。  使用零长度或空白字符串会逐个拆分各个字符。  匹配的分隔符不会在结果中返回。  如果找不到匹配的分隔符，整个文本字符串会作为一个结果返回。

使用 [Concat](function-concatenate.md) 函数可重新组合字符串（不带分隔符）。  

## <a name="syntax"></a>语法
Split( Text, Separator )

* Text - 必需。  要拆分的文本。
* Separator - 必需。  拆分字符串时要使用的分隔符。  可以是零个、一个或多个字符。

## <a name="examples"></a>示例
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," )** |根据逗号分隔符拆分各种水果。  由于拆分仅以逗号（而不是后面的空格）为依据，因此 "&nbsp;Oranges" 和 "&nbsp;Bananas" 前面会有空格。 |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| **TrimEnds( Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," ) )** |与上一示例基本相同。不同之处在于，在此示例中，[TrimEnds 函数](function-trim.md)对 Split 生成的单列表执行操作，删除了空格。 我们本来也可以使用分隔符“,&nbsp;”（即逗号后面有空格），但这并不适用于不含空格或有两个空格的情况。 |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| **Split( "08/28/17", "/" )** |使用正斜线作为分隔符来拆分日期。 |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |
| **Split( "Hello,&nbsp;World", "," )** |使用逗号作为分隔符来拆分词语。  第二个结果以空格开头，因为逗号后面紧跟此字符。 |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| **Split( "Hello,&nbsp;World", "o" )** |使用字符“o”作为分隔符来拆分字符串。 |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| **Split( "Hello,&nbsp;World", "l" )** |使用单字符“l”作为分隔符来拆分字符串。 由于 Hello 中的两个 l 之间没有任何字符，因此返回值 blank。 |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| **Split( "Hello,&nbsp;World", "ll" )** |使用双字符“ll”作为分隔符来拆分字符串。 |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| **Split( "Hello,&nbsp;World", "%" )** |使用百分号作为分隔符来拆分字符串。 由于字符串中没有此分隔符，因此整个字符串作为一个结果返回。 |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| **Split( "Hello,&nbsp;World", "" )** |使用空字符串作为分隔符（零个字符）来拆分字符串。 这会逐个拆分字符串中的每个字符。 |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

