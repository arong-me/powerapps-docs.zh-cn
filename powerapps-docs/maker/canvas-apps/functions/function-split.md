---
title: Split 函数 | Microsoft 文档
description: PowerApps 中 Split 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72f92477cc8c942ee0274267c5bcb13094681873
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984144"
---
# <a name="split-function-in-powerapps"></a>PowerApps 中的 Split 函数
将文本字符串拆分成子字符串表。

## <a name="description"></a>描述
Split 函数将文本字符串拆分成子字符串表。  Split 可用于拆分以逗号分隔的列表、在各日期部分之间使用斜线的日期，并适用于使用定义完善的分隔符的其他情况。  

分隔符字符串用于拆分文本字符串。  分隔符可以是零个、一个或多个字符，整体可以在文本字符串中找到匹配项。  使用零长度或空白字符串会逐个拆分各个字符。  匹配的分隔符不会在结果中返回。  如果找不到匹配的分隔符，整个文本字符串会作为一个结果返回。

使用 **[Concat](function-concatenate.md)** 函数重新组合不带分隔符的字符串。 
 
使用 **[MatchAll](function-ismatch.md)** 函数可使用正则表达式拆分字符串。

这些示例演示了如何使用**Split**和 **[First](function-first-last.md)** **[函数来](function-first-last.md)** 提取单个分隔的子字符串。  对于熟悉正则表达式的人员而言， **[Match](function-ismatch.md)** 函数通常是更简洁、更强大的选择。

## <a name="syntax"></a>语法
Split( Text, Separator )

* Text - 必需。  要拆分的文本。
* Separator - 必需。  拆分字符串时要使用的分隔符。  可以是零个、一个或多个字符。

## <a name="examples"></a>示例

### <a name="basic-usage"></a>基本用法

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| `Split( "Apples, Oranges, Bananas", "," )` |根据逗号分隔符拆分各种水果。  由于拆分仅以逗号（而不是后面的空格）为依据，因此 "&nbsp;Oranges" 和 "&nbsp;Bananas" 前面会有空格。 |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| `TrimEnds( Split( "Apples, Oranges, Bananas", "," ) )` |与上一示例基本相同。不同之处在于，在此示例中，[TrimEnds 函数](function-trim.md)对 Split 生成的单列表执行操作，删除了空格。 我们本来也可以使用分隔符“,&nbsp;”（即逗号后面有空格），但这并不适用于不含空格或有两个空格的情况。 |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| `Split( "08/28/17", "/" )` |使用正斜线作为分隔符来拆分日期。 |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |

### <a name="different-delimiters"></a>不同分隔符

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| `Split( "Hello, World", "," )` |使用逗号作为分隔符来拆分词语。  第二个结果以空格开头，因为逗号后面紧跟此字符。 |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| `Split( "Hello, World", "o" )` |使用字符“o”作为分隔符来拆分字符串。 |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| `Split( "Hello, World", "l" )` |使用单字符“l”作为分隔符来拆分字符串。 由于 Hello 中的两个 l 之间没有任何字符，因此返回值 blank。 |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| `Split( "Hello, World", "ll" )` |使用双字符“ll”作为分隔符来拆分字符串。 |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| `Split( "Hello, World", "%" )` |使用百分号作为分隔符来拆分字符串。 由于字符串中没有此分隔符，因此整个字符串作为一个结果返回。 |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| `Split( "Hello, World", "" )` |使用空字符串作为分隔符（零个字符）来拆分字符串。 这会逐个拆分字符串中的每个字符。 |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

### <a name="substring-extraction"></a>子字符串提取

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| `First( Split( Last( Split( "Bob Jones <bob.jones@contoso.com>", "<" ) ).Result, ">" ) ).Result` | 根据开始分隔符（<）分隔字符串，并在**最后**的分隔符右侧提取字符串。  然后，该公式会根据右分隔符（>）拆分该结果，并在**右侧**提取分隔符左侧的字符串。 | "bob.jones@contoso.com" |
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>.+)>" ).email` | 执行与上一示例相同的基于分隔符的提取，但使用**Match**函数和正则表达式。 | "bob.jones@contoso.com" |

