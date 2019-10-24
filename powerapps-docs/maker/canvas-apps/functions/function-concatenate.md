---
title: Concat 和 Concatenate 函数 | Microsoft 文档
description: PowerApps 中 Concat 和 Concatenate 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "71992886"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps 中的 Concat 和 Concatenate 函数

将[表](../working-with-tables.md)中的文本和字符串连成单个字符串。

## <a name="description"></a>描述

**Concatenate** 函数可将混合的单独字符串和单列表中的字符串连接起来。 将此函数与单个字符串一起使用时，它等效于使用 **&** [运算符](operators.md)。

**Concat** 函数可将应用于表中所有[记录](../working-with-tables.md#records)的公式的结果串联起来，从而产生单个字符串。 使用这个函数可汇总表的字符串，就像 **[Sum](function-aggregates.md)** 函数可以汇总数字一样。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

使用[**split**](function-split.md)或[**MatchAll**](function-ismatch.md)函数将字符串拆分为子字符串的表。

## <a name="syntax"></a>语法

**Concat**( *Table*, *Formula* )

- *Table* - 必需。  要运算的表。
- *Formula* - 必需。  要对表中的记录应用的公式。

**Concatenate**( *String1* [, *String2*, ...] )

- *String(s)* - 必需。  单独字符串或单列表中字符串的混合形式。

## <a name="examples"></a>示例

本节中的示例使用以下全局变量：

- **FirstName** = "Jane"
- **LastName** = "Doe"
- 具有两列和四行的**产品** =  ![Table ](media/function-concatenate/products.png)

若要在应用中创建这些全局变量，请插入[**按钮**](../controls/control-button.md)控件，并将其**OnSelect**属性设置为以下公式：

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

选择按钮（在按住 Alt 键的同时单击该按钮）。

### <a name="concatenate-function-and-the--operator"></a>连接函数和 & 运算符

对于这些示例，请将 "[**标签**](../controls/control-text-box.md)" 控件的 " **Text** " 属性设置为下表的第一列中的公式。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **连接（&nbsp;LastName，&nbsp; "，&nbsp;"，&nbsp;FirstName &nbsp;）** | 连接**LastName**中的值、字符串 **"，"** （逗号后跟一个空格）和**FirstName**中的值。 | "Doe，&nbsp;Jane" |
| **LastName &nbsp; & &nbsp; "、&nbsp;" &nbsp; & &nbsp;FirstName** | 与前面的示例相同，但使用 **&** 运算符而不是函数。 | "Doe，&nbsp;Jane" |
| **连接（&nbsp;FirstName，&nbsp; "&nbsp;"，&nbsp;LastName &nbsp;）** | 连接**FirstName**中的值、字符串 **""** （单个空格）和**LastName**中的值。 | "Jane &nbsp;Doe" |
| **FirstName &nbsp; & &nbsp; "&nbsp;" &nbsp; & &nbsp;LastName** | 与上面的示例相同，使用 **&** 运算符而不是函数。 | "Jane &nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>与单列表连接

在此示例中，添加一个空白的垂直[**库**](../controls/control-gallery.md)控件，将其**Items**属性设置为下一个表中的公式，然后在库模板中添加标签。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **连接（"名称： &nbsp;"，&nbsp;Products，"，&nbsp;Type： &nbsp;"，&nbsp;Products 类型）** | 对于**Products**表中的每个记录，连接字符串 **"name："** 、产品的名称、字符串 **"，type："** 和产品的类型。  | ![产品表](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 函数

对于这些示例，请将标签的 " **Text** " 属性设置为下表的第一列中的公式。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Concat （Products，Name & "，"）** | 计算每个**产品**记录的表达式**名称 & "，"** ，并将结果连接成单个文本字符串。  | "Violin，&nbsp;Cello，&nbsp;Trumpet，&nbsp;" |
| **Concat （Filter （&nbsp;Products，&nbsp;Type &nbsp; = &nbsp; "String" &nbsp;），Name & "，"）** | 为满足筛选器**类型 = "String"** 的**产品**的每个记录计算公式**名称 & "，"** ，并将结果连接到一个文本字符串。   | "Violin，&nbsp;Cello，&nbsp;" |

### <a name="trimming-the-end"></a>剪裁结束

最后两个示例在结果末尾添加一个额外的 "，"。 函数在表中的每个记录的**名称**值后面追加一个逗号和一个空格，包括最后一条记录。

在某些情况下，这些额外字符并不重要。 例如，如果在标签中显示结果，则不会显示单空格分隔符。 如果要删除这些额外字符，请使用[**Left**](function-left-mid-right.md)或[**Match**](function-ismatch.md)函数。

对于这些示例，请将标签的 " **Text** " 属性设置为下表的第一列中的公式。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Left （Concat （&nbsp;Products，&nbsp;Name &nbsp; & &nbsp; "，&nbsp;" &nbsp;），Len （&nbsp;Concat （&nbsp;Products，0Name 1 2 3 "，4" 5） 6） 7 8 92）** | 返回**Concat**的结果，但会删除最后两个字符，这些字符构成无关分隔符。 | "Violin，&nbsp;Cello，&nbsp;Trumpet" |
| **Match （Concat （&nbsp;Products，&nbsp;Name &nbsp; & &nbsp; "，&nbsp;" &nbsp;），"^ （？&lt;trim &gt;. *），0 $ "）** | 返回从文本字符串（^）的开头到末尾（$）的**Concat**的字符，但不包括不需要的逗号和空格。 | "Violin，&nbsp;Cello，&nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split 和 MatchAll

如果通过分隔符使用了**Concat** ，则可以通过组合**Split**和**MatchAll**函数来撤消操作。

对于这些示例，请在下表中添加一个空白的垂直库，将其**Items**属性设置为一个公式，然后在库模板中添加一个标签。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Split （Concat （&nbsp;Products，&nbsp;Name &nbsp; & &nbsp; "，&nbsp;" &nbsp;），"，"）** | 拆分文本字符串，分隔符为 **"，"** 。 字符串以逗号和空格结尾，因此结果中的最后一行是空字符串。  | ![Table](media/function-concatenate/split.png) |
| **MatchAll （Concat （&nbsp;Products，&nbsp;Name &nbsp; & &nbsp; "，&nbsp;" &nbsp;），"[^ \s，] +"）。FullMatch** | 根据不为空格或逗号的字符拆分文本字符串。 此公式将删除字符串末尾的额外逗号和空格。 | ![Table](media/function-concatenate/matchall.png)