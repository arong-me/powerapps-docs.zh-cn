---
title: If 和 Switch 函数 | Microsoft 文档
description: Power Apps 中 If 和 Switch 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 07924ea46dd0914fbeaf5d0fef24bb3cdc543d6c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730845"
---
# <a name="if-and-switch-functions-in-power-apps"></a>Power Apps 中的 If 和 Switch 函数
确定集中的任何条件是否为 true (If)，或确定公式的结果是否与集中的任何值一致 (Switch)，再返回结果或执行操作。

## <a name="description"></a>描述
If 函数会一直测试一个或多个条件，直到结果为 true 时为止。 如果结果为 true，将返回相应的值。 否则，将返回默认值。 无论属于上述哪种情况，返回的值可以是要显示的字符串、要求值的公式或另一种形式的结果。

Switch 函数先对公式求值，再确定结果是否与指定序列中的任何值一致。 如果找到匹配值，将返回相应的值。 否则，将返回默认值。 无论属于上述哪种情况，返回的值可以是要显示的字符串、要求值的公式或另一种形式的结果。

虽然 If 和 Switch 函数非常相似，但应使用最适合自身情况的函数：

* 使用 If 函数对一个条件求值。 此函数的最常见语法为 If( Condition, ThenResult, DefaultResult )，提供其他编程工具中常见的“if …  then … else …” 模式。
* 使用 If 函数对多个不相关条件求值。 在 Power Apps （与 Microsoft Excel 不同）中，可以指定多个条件，而无需嵌套**If**公式。
* 使用 Switch 对一个条件求值，以进行多次匹配。 在这种情况下，还可以使用 If 函数，但需要为每次匹配重复执行公式。

可以在[行为公式](../working-with-formulas-in-depth.md)中结合使用这两个函数，在两个或多个操作之间形成分支。 操作只由一个分支触发。 将按顺序对条件和匹配进行求值，如果条件为 true 或找到匹配项，将停止求值。

如果没有条件为 true、找不到任何匹配项且未指定默认结果，将返回 Blank。

## <a name="syntax"></a>语法
If( Condition, ThenResult [, DefaultResult ] )<br>If( Condition1, ThenResult1 [, Condition2, ThenResult2, ... [ , DefaultResult ] ] )

* *Condition(s)* - 必需。 要测试是否为 true 的公式。 此类公式通常包含比较[运算符](operators.md)（如 <、> 和 =）和测试函数（如 [IsBlank](function-isblank-isempty.md) 和 [IsEmpty](function-isblank-isempty.md)）。
* ThenResult(s) - 必需。 对计算结果为 **true** 的条件返回的对应值。
* DefaultResult - 可选。 没有条件求值为 true 时返回的值。  如果未指定此参数，则将返回空白。

Switch(Formula, Match1, Result1 [, Match2, Result2, ... [, DefaultResult ] ] )

* *Formula* - 必需。 为进行匹配而求值的公式。  此公式仅求值一次。
* Match(s) - 必需。 要与公式结果比较的值。  如果找到完全匹配项，将返回相应的结果。
* *Result(s)* - 必需。 找到完全匹配项时返回的相应值。
* DefaultResult - 可选。 如果找不到匹配项，将返回此值。 如果未指定此参数，则将返回空白。

## <a name="examples"></a>示例
### <a name="values-in-formulas"></a>公式中的值
在下面这些示例中，“滑块”控件（名为“Slider1”）的值为“25”。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1" )** |条件为 **true**，并返回相应结果。 |“Result1” |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", "Result2" )** |条件为 **true**，并返回相应结果。 |“Result1” |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1" )** |条件为 false，且未提供 DefaultResult。 |*blank* |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", "Result2" )** |条件为 false，但提供了 DefaultResult，将返回此结果。 |“Result2” |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", Slider1.Value&nbsp;>&nbsp;0, "Result2" )** |第一个条件为 **true**，并返回相应结果。 第二个条件也为 true，但未进行求值，因为它在参数列表中的出现时间要晚于比求值为 true 的条件。 |“Result1” |
| **If( IsBlank(&nbsp;Slider1.Value&nbsp;), "Result1", IsNumeric(&nbsp;Slider1.Value&nbsp;), "Result2" )** |第一个条件为 false，因为滑块不是 blank。 第二个条件为 **true**，因为滑块的值是数字，并返回相应结果。 |“Result2” |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", Slider1.Value&nbsp;>&nbsp;50, "Result2", "Result3")** |第一个和第二个条件均为 false，但提供了 DefaultResult，将返回此结果。 |“Result3” |
| **Switch( Slider1.Value, 25, "Result1" )** |滑块的值与要检查的第一个值一致，将返回相应的结果。 |“Result1” |
| **Switch( Slider1.Value, 20, "Result1", 25, "Result2", 30, "Result3" )** |滑块的值与要检查的第二个值一致，将返回相应的结果。 |“Result2” |
| **Switch( Slider1.Value, 20, "Result1", 10, "Result2", 0, "Result3", "DefaultResult" )** |滑块的值与要检查的任何值都不一致。  因为提供了 DefaultResult，所以将返回此结果。 |"DefaultResult" |

### <a name="branching-in-behavior-formulas"></a>在行为公式中分支
在下面这些示例中，用户在名为“FirstName”的“[文本输入](../controls/control-text-input.md)”控件中键入的值为“John”。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **If （！IsBlank （FirstName），导航（&nbsp;Screen1，Screentransition.none））** |条件为 true，因此将运行 [Navigate](function-navigate.md) 函数。 可使用 **[IsBlank](function-isblank-isempty.md)** 函数测试所需的窗体字段是否已填充。  如果 FirstName 为 [blank](function-isblank-isempty.md)，此公式不会产生任何影响。 |**true**<br><br>显示更改为 **Screen1**。 |
| **If( IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ), Back() )** |没有 ! 运算符，条件为 false，因此不会运行 [Navigate](function-navigate.md) 函数。 因为 [Back](function-navigate.md) 函数作为 DefaultResult 提供，所以将运行此函数。 |**true**<br><br>将重新显示之前显示的屏幕。 |
| **Switch( FirstName.Text, "Carlos", Navigate(&nbsp;Screen1, ScreenTransition.None ), "Kirstin", Navigate( Screen2, ScreenTransition.None ), "John", Navigate( Screen3, ScreenTransition.None ) )** |将 FirstName.Text 的值与“Carlos”、“Kirstin”和“John”（按此顺序）进行比较。 因为找到与“John”匹配的项，所以应用将转到 Screen3。 |**true**<br><br>切换显示 Screen3。 |

### <a name="step-by-step"></a>分步操作
1. 添加“[文本输入](../controls/control-text-input.md)”控件，再将它命名为“Text1”（如果默认名称不是这样的话）。
2. 在“Text1”中，键入“30”。
3. 添加一个“标签”控件，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式：<br>
   **If( Value(Text1.Text) < 20, "Order MANY more!", Value(Text1.Text) < 40, "Order more!", Text1.Text )**
   
    此时，“标签”控件显示“订购更多！”， 因为“Text1”的值大于 20 但小于 40。
4. 在 **Text1** 中，键入 **15**。
   
    此时，“标签”控件显示“订购更多更多！” 因为“Text1” 的值小于 20。
5. 在“Text1”中，键入“50”。
   
    此时，“标签”控件显示所键入的值，因为“Text1”的值大于 40。

