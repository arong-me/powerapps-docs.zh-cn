---
title: And、Or 和 Not 函数 | Microsoft 文档
description: PowerApps 中 And、Or 和 Not 函数的参考信息，包括语法和示例
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
ms.openlocfilehash: a2b04e6a752ade561ec1b95658bcacda759b1a1c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992562"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>PowerApps 中的 And、Or 和 Not 函数

布尔逻辑函数，常用于操作比较结果和测试结果。

## <a name="description"></a>描述

如果 **And** 函数的所有参数均为 **true**，则此函数返回 **true**。

如果 **Or** 函数的任何参数为 **true**，则此函数返回 **true**。

如果 **Not** 函数的参数为 **false**，则此函数返回 **true**；如果其参数为 **true**，则返回 **false**。

这些函数的工作方式与在 Excel 中的工作方式相同。 你还可以使用[运算符](operators.md)来执行相同的操作，方法是使用 Visual Basic 或 JavaScript 语法：

| 函数表示法 | Visual Basic 运算符表示法 | JavaScript 运算符表示法 |
| -------------|------------|--------|
| **And （x，y）** | **x 和 y** | **x & & y** |
| **Or （x，y）** | **x 或 y** | **x &#124; &#124; y** |
| **不（x）** | **非 x** | **!x-blade** |

这些函数使用逻辑值。 不能直接向其传递数字或字符串;相反，您必须进行比较或测试。 例如，如果**x**大于**1**，则此逻辑公式**x > 1**的计算结果为布尔值**true** 。 如果**x**小于**1**，则公式的计算结果为**false**。

## <a name="syntax"></a>语法

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 必需。  要计算和运算的逻辑公式。

## <a name="examples"></a>示例

本节中的示例使用以下全局变量：

- **@no__t-** 1*false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

若要在应用中创建这些全局变量，请插入[**按钮**](../controls/control-button.md)控件，并将其**OnSelect**属性设置为以下公式：

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

选择按钮（在按住 Alt 键的同时单击），然后将 "[**标签**](../controls/control-text-box.md)" 控件的 " **Text** " 属性设置为下表第一列中的公式。

| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| **And （a，b）** | 测试**a**和**b**的值。  其中一个参数为*false*，因此该函数返回*false*。 | *false* |
| **a 和 b** | 与前面的示例相同，使用 Visual Basic 表示法。 | *false* |
| **& & b** | 与上面的示例相同，使用 JavaScript 表示法。 | *false* |
| **Or （a，b）** | 测试**a**和**b**的值。 其中一个参数为*true*，因此该函数返回*true*。 | *true* |
| **a 或 b** | 与前面的示例相同，使用 Visual Basic 表示法。 | *true* |
| **a &#124; &#124; b** | 与上面的示例相同，使用 JavaScript 表示法。 | *true* |
| **Not （a）** | 测试**的值。** 参数为*false*，因此函数返回相反的结果。 | *true* |
| **不是** | 与前面的示例相同，使用 Visual Basic 表示法。 | *true* |
| **!的** | 与上面的示例相同，使用 JavaScript 表示法。 | *true* |
| **Len （@no__t 1 @ no__t-2） &nbsp; @ no__t-4 @ no__t-520 And @ no__t-6Not @ no__t-7IsBlank （&nbsp;s @ no__t）** | 测试**的长度**是否小于20以及它是否不是**空**值。 长度小于20，且值不为空。 因此，结果为*true*。 | *true* |
| **或（&nbsp;Len （&nbsp; @ no__t） &nbsp; @ no__t-5 @ no__t-610，x @ no__t-7 @ no__t-8 @ no__t-9100，y @ no__t-10 @ no__t-11 @ no__t-12100 @ no__t-13）** | 测试**的长度**是否小于10， **x**是否小于100，以及**y**是否小于100。 第一个和第三个参数为 false，但第二个参数为 true。 因此，该函数返回*true*。 | *true* |
| **Not IsBlank （&nbsp; @ no__t-2）** | 测试**s**是否为*空*，这将返回*false*。 返回的结果**不**是此结果的相反*值*。 | *true* |