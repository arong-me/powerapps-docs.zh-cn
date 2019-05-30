---
title: Concat 和 Concatenate 函数 | Microsoft 文档
description: PowerApps 中 Concat 和 Concatenate 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 889f612f3da208d4edfccc43a579ced07933b40d
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216031"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps 中的 Concat 和 Concatenate 函数

将[表](../working-with-tables.md)中的文本和字符串连成单个字符串。

## <a name="description"></a>描述

**Concatenate** 函数可将混合的单独字符串和单列表中的字符串连接起来。 当使用单个字符串中使用此函数时，它相当于使用 **&** [运算符](operators.md)。

**Concat** 函数可将应用于表中所有[记录](../working-with-tables.md#records)的公式的结果串联起来，从而产生单个字符串。 使用这个函数可汇总表的字符串，就像 **[Sum](function-aggregates.md)** 函数可以汇总数字一样。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

使用[**拆分**](function-split.md)或[ **MatchAll** ](function-ismatch.md)函数将字符串拆分成子字符串表。

## <a name="syntax"></a>语法

**Concat**( *Table*, *Formula* )

- *Table* - 必需。  要运算的表。
- *Formula* - 必需。  要对表中的记录应用的公式。

**Concatenate**( *String1* [, *String2*, ...] )

- *String(s)* - 必需。  单独字符串或单列表中字符串的混合形式。

## <a name="examples"></a>示例

在本部分中的示例使用这些全局变量：

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **产品** = ![具有两个列和四行的表](media/function-concatenate/products.png)

若要在应用中创建这些全局变量，插入[**按钮**](../controls/control-button.md)控件，并设置其**OnSelect**属性设为此公式：

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

选择按钮 （通过单击时按住 Alt 键）。

### <a name="concatenate-function-and-the--operator"></a>Concatenate 函数和 & 运算符

对于这些示例中，设置**文本**的属性[**标签**](../controls/control-text-box.md)控件的公式从下一个表的第一列。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Concatenate(&nbsp;LastName,&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | 连接中的值**LastName**，该字符串 **"，"** （一个逗号后跟一个空格），和中的值**FirstName**。 | "Doe&nbsp;Jane" |
| **LastName&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | 除使用前一示例相同 **&** 运算符而不是函数。 | "Doe&nbsp;Jane" |
| **Concatenate(&nbsp;FirstName,&nbsp;"&nbsp;",&nbsp;LastName&nbsp;)** | 连接中的值**FirstName**，该字符串 **""** （单个空格） 和中的值**LastName**。 | "Jane&nbsp;Doe" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;LastName** | 与上面的示例中，同一个使用 **&** 运算符而不是函数。 | "Jane&nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>含有单列的表连接

对于此示例中，添加空白垂直[**库**](../controls/control-gallery.md)控件，将其**项**属性设为公式中下一个表，然后将标签添加库模板中。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Concatenate( "Name:&nbsp;",&nbsp;Products.Name, ",&nbsp;Type:&nbsp;",&nbsp;Products.Type )** | 中每个记录**产品**表中，将连接字符串 **"名称:"** ，产品，该字符串的名称 **"，类型:"** 和产品的类型。  | ![产品表](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 函数

对于这些示例中，设置**文本**从下一个表的第一列的公式标签的属性。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Concat( Products, Name & ", " )** | 计算表达式的值**名称 &"、"** 针对每条记录**产品**，并将结果连在一起的单个文本字符串。  | "小提琴，&nbsp;Cello，&nbsp;喇叭示意发出通知，&nbsp;" |
| **Concat( Filter(&nbsp;Products,&nbsp;Type&nbsp;=&nbsp;"String"&nbsp;), Name & ", " )** | 评估公式**名称 &"、"** 针对每条记录**产品**满足筛选器**类型 ="String"** ，并将结果连接成单个文本字符串。   | "小提琴，&nbsp;Cello，&nbsp;" |

### <a name="trimming-the-end"></a>剪裁结束

最后两个示例包括一个额外"，"结果的末尾。 该函数将追加一个逗号和空格**名称**中包括的最后一个记录的表的每个记录的值。

在某些情况下，这些额外的字符没有影响。 例如，只留下在标签中显示结果时，不会显示分隔符。 如果你想要删除这些额外的字符，使用[**左**](function-left-mid-right.md)或[**匹配**](function-ismatch.md)函数。

对于这些示例中，设置**文本**从下一个表的第一列的公式标签的属性。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Left( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len(&nbsp;Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2 )** | 返回的结果**Concat**但中移除窗体中的多余的分隔符的最后两个字符。 | "小提琴，&nbsp;Cello，&nbsp;喇叭示意发出通知" |
| **Match( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^(?&lt;trim&gt;.*),&nbsp;$" ).trim** | 返回的字符**Concat**从开头到末尾 （$） 的文本字符串 (^)，但不包括不需要的逗号和末尾的空格。 | "小提琴，&nbsp;Cello，&nbsp;喇叭示意发出通知" |

### <a name="split-and-matchall"></a>拆分和 MatchAll

如果您使用了**Concat**分隔符，使用中，您可以撤消该操作通过组合**拆分**并**MatchAll**函数。

这些示例中，添加一个空白、 垂直库，在搜索框中设置其**项**属性设为公式中下一个表，然后将标签添加库模板中。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **Split( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), ", " )** | 使用分隔符拆分的文本字符串 **"，"** 。 字符串结尾于逗号和空格，因此结果中的最后一行是空字符串。  | ![Table](media/function-concatenate/split.png) |
| **MatchAll( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "[^\s,]+" ).FullMatch** | 将拆分基于不是空格或逗号分隔的字符的文本字符串。 此公式中删除多余的逗号和空格的字符串的末尾。 | ![Table](media/function-concatenate/matchall.png)