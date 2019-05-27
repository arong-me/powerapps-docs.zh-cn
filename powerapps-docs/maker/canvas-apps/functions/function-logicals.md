---
title: And、Or 和 Not 函数 | Microsoft 文档
description: PowerApps 中 And、Or 和 Not 函数的参考信息，包括语法和示例
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
ms.openlocfilehash: 4eb020d854549b6dc8878f07ae26390523a1bc03
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215981"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>PowerApps 中的 And、Or 和 Not 函数

布尔逻辑函数，常用于操作比较结果和测试结果。

## <a name="description"></a>描述

如果 **And** 函数的所有参数均为 **true**，则此函数返回 **true**。

如果 **Or** 函数的任何参数为 **true**，则此函数返回 **true**。

如果 **Not** 函数的参数为 **false**，则此函数返回 **true**；如果其参数为 **true**，则返回 **false**。

这些函数与在 Excel 中的工作方式相同。 此外可以使用[运算符](operators.md)来执行这些相同的操作，使用 Visual Basic 或 JavaScript 的语法：

| 函数表示法 | Visual Basic 运算符表示法 | JavaScript 运算符表示法 |
| -------------|------------|--------|
| **And( x, y )** | **x 和 y** | **x & & y** |
| **Or( x, y )** | **x 或 y** | **x &#124;&#124; y** |
| **Not( x )** | **不 x** | **!x** |

这些函数使用逻辑值。 不能将其传递一个数字或字符串直接调用相反，必须进行比较或测试。 例如，此逻辑公式**x > 1**的计算结果为布尔值**true**如果**x**大于**1**。 如果**x**是小于**1**，该公式的计算结果为**false**。

## <a name="syntax"></a>语法

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 必需。  要计算和运算的逻辑公式。

## <a name="examples"></a>示例

在本部分中的示例使用这些全局变量：

- **a** = *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** ="Hello World"

若要在应用中创建这些全局变量，插入[**按钮**](../controls/control-button.md)控件，并设置其**OnSelect**属性设为此公式：

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

（通过单击时按住 Alt 键），选择该按钮，然后设置**文本**的属性[**标签**](../controls/control-text-box.md)控件到下一个表的第一列中的公式。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **And( a, b )** | 测试的值并**b**。  一个参数是*false*，因此该函数将返回*false*。 | *false* |
| **And b** | 与上述示例中，使用 Visual Basic 表示法相同。 | *false* |
| **a && b** | 与上述示例中，使用 JavaScript 表示法相同。 | *false* |
| **Or( a, b )** | 测试的值并**b**。 一个参数是 *，则返回 true*，因此该函数将返回*true*。 | *true* |
| **Or b** | 与上述示例中，使用 Visual Basic 表示法相同。 | *true* |
| **a &#124;&#124; b** | 与上述示例中，使用 JavaScript 表示法相同。 | *true* |
| **不 (a)** | 测试的值。 参数是*false*，因此该函数返回相反的结果。 | *true* |
| **不** | 与上述示例中，使用 Visual Basic 表示法相同。 | *true* |
| **!的** | 与上述示例中，使用 JavaScript 表示法相同。 | *true* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 和&nbsp;不&nbsp;IsBlank (&nbsp;s&nbsp;)** | 测试是否的长度**s**小于 20，并且它是否不**空白**值。 长度小于 20，且值不是空的。 因此，结果是 *，则返回 true*。 | *true* |
| **或者 (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;月 10 日，x&nbsp;<&nbsp;100，y&nbsp;<&nbsp;100&nbsp;)** | 测试是否的长度**s**是否为小于 10， **x**小于 100，以及是否**y**小于 100。 第一个和第三个参数都为 false，但第二个是 true。 因此，该函数返回 *，则返回 true*。 | *true* |
| **Not IsBlank(&nbsp;s&nbsp;)** | 测试是否**s**是*空白*，它将返回*false*。 **不**返回此结果，即反*true*。 | *true* |