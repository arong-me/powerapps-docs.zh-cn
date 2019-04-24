---
title: Abs、Exp、Ln、Power 和 Sqrt 函数 | Microsoft 文档
description: PowerApps 中 Abs、Sqrt 和其他函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 95406bff477a4d84a6125225ffc1e158ffb8c19a
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544000"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-powerapps"></a>PowerApps 中的 Abs、Exp、Ln、Power 和 Sqrt 函数
计算绝对值、自然对数、平方根和 *e* 或任意数字的指定次方值结果。

## <a name="description"></a>描述
**Abs** 函数返回参数的非负值。 **Abs** 返回负数的绝对值。

**Exp** 函数返回 *e* 的参数次方值。  超越数 *e* 的一次方值为 2.7182818...

**Ln** 函数返回参数的自然对数（以 *e* 为底）。

**Power** 函数返回数字的次方值。  相当于使用 [**^** 运算符](operators.md)。

**Sqrt** 函数返回参数的平方根。

如果你传递一个数字，则返回一个视调用函数而定的结果值。  如果你传递包含数字的单列[表](../working-with-tables.md)，则返回单列表结果值，参数表中每条记录都对应一个结果。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。  

如果参数的结果值未经定义，则结果为*空白*。  例如，在求负数的平方根和对数时可能会遇到这种情况。

## <a name="syntax"></a>语法
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number* - 必需。 要计算的数字。

**Power**( *Base*, *Exponent* )

* *Base* - 必需。 计算次方值时的底数。
* *Exponent* - 必需。 计算底数次方值时的指数。

**Abs**( *SingleColumnTable* )<br>**Exp**( *SingleColumnTable* )<br>**Ln**( *SingleColumnTable* )<br>**Sqrt**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要计算的单列表数字。

## <a name="examples"></a>示例
### <a name="single-number"></a>单个数字

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Abs( -55 )** |返回不带负号的数字。 |55 |
| **Exp( 2 )** |返回 *e* 的 2 次方值，或 *e* \* *e* 结果值。 |7.389056... |
| **Ln( 100 )** |返回数字 100 的自然对数（以 *e* 为底）。 |4.605170... |
| **Power( 5, 3 )** |返回 5 的 3 次方值 ，或 5 \* 5 \* 5 结果值。 |125 |
| **Sqrt( 9 )** |返回 9 的平方根。 |3 |

### <a name="single-column-table"></a>单列表
本部分中的示例使用名为 **ValueTable** 的[数据源](../working-with-data-sources.md)，其中包括以下数据：

![](media/function-numericals/values.png)

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Abs(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的绝对值。 |<style> img { max-width: none } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;ValueTable&nbsp;)** |返回 *e* 的表中每个数字次方值。 |<style> img { max-width: none } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的自然对数。 |<style> img { max-width: none } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的平方根。 |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>分步示例
1. 添加 **[“文本输入”](../controls/control-text-input.md)** 控件，然后将其命名为“Source”。
2. 添加一个“标签”控件，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式：
   <br>
   **Sqrt( Value( Source.Text ) )**
3. 在“源”中键入数字，然后确认“标签”控件中是否显示所键入数字的平方根。

