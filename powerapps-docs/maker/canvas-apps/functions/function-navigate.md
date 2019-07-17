---
title: Back 和 Navigate 函数 | Microsoft 文档
description: PowerApps 中 Back 和 Navigate 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e57cc541c753ff3f24f66a78c6e30d6e5683b41a
ms.sourcegitcommit: 57dfad065318263e162e949e26b5c2684ba0dccb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828174"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Microsoft PowerApps 中的 Back 和 Navigate 函数

更改显示的屏幕。

## <a name="overview"></a>概述

大多数应用都包含多个屏幕。  **Back** 和 **Navigate** 函数可用于更改所显示的屏幕。 例如，如果你希望用户在选中某个按钮后显示其他屏幕，请将该按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为一个包含 **Navigate** 函数的公式。 在这个公式中，你可以指定视觉变换效果（比如 **Fade**）来控制屏幕切换方式。  

**Back** 和 **Navigate** 只能更改当前显示的屏幕。 当前未显示的屏幕仍然在后台运行。 可以生成引用的其他屏幕上的控件属性的公式。 例如，用户可以更改一个屏幕上滑块的值，导航到在公式中，使用该值的另一个屏幕并确定它如何影响新屏幕中会发生什么情况。 然后，用户可以导航回原来的屏幕，并确认滑块保留了其值。

当用户在屏幕之间导航时，[上下文变量](../working-with-variables.md#use-a-context-variable)也会保留。 你可以使用 **Navigate** 设置公式会显示的屏幕的一个或多个上下文变量，这是从屏幕外部设置上下文变量的唯一方法。 这个方法可用于将参数传递到屏幕。 如果你使用过另一款编程工具，就会发现这个方法与将参数传递给过程非常相似。

可以仅在使用这两种函数[行为公式](../working-with-formulas-in-depth.md)。

## <a name="navigate"></a>Navigate

在第一个参数中，指定要显示的屏幕的名称。  

 在第二个参数中，指定旧屏幕切换为新屏幕的方式：

| Transition 参数 | 描述 | 演示 |
| --- | --- | --- |
| **ScreenTransition.Cover** |新屏幕滑入视图中，右到左移动，以覆盖当前屏幕。 | ![屏幕转换封面动画](media/function-navigate/cover.gif) |
| **ScreenTransition.CoverRight** |视图中，移动到新的屏幕幻灯片从左到右，以覆盖当前屏幕。 | ![屏幕转换封面右动画](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |当前以显示新屏幕的屏幕淡化。 | ![屏幕转换淡入淡出动画](media/function-navigate/fade.gif) |
| **ScreenTransition.None** （默认值） |新屏幕快速替换当前屏幕。 | ![屏幕过渡无动画](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | 当前屏幕滑出视图中，右到左移动，以发现新屏幕。 | ![屏幕转换发现动画](media/function-navigate/uncover.gif) |
| **ScreenTransition.UnCoverRight** | 从视图中，移动的当前屏幕幻灯片从左到右，以发现新屏幕。 | ![屏幕转换发现正确的动画](media/function-navigate/uncoverright.gif) |

可以使用 **Navigate** 创建或更新的新屏幕的上下文变量。 第三个参数是可选的，它可用于传递一条[记录](../working-with-tables.md#records)，其中包含上下文变量名称（以[列](../working-with-tables.md#columns)名称的形式）和上下文变量的新值。  这条记录就是用于 **[UpdateContext](function-updatecontext.md)** 函数的记录。

设置旧屏幕的 **[OnHidden](../controls/control-screen.md)** 属性和/或新屏幕的 **[OnVisible](../controls/control-screen.md)** 属性，以在过渡期间进行其他更改。 **App.ActiveScreen** 属性将更新以反映更改。

**导航**正常情况下返回**true**将返回，但**false**如果遇到错误。

## <a name="back"></a>Back

**回**函数将返回到最近显示的屏幕。

每个**Navigate**调用时，应用可跟踪出现在屏幕和转换。 您可以使用连续**回**调用，以将用户返回到屏幕出现时启动应用。

当**回**默认情况下使用函数运行时，反向转换。 例如，如果通过出现一个屏幕**CoverRight**转换**回**使用**UnCover** （是左侧） 返回。  **淡**并**None**为他们自己的逆方法。 传递的可选参数**回**强制某一特定转换。

**回到**正常情况下返回**true**但返回**false**如果用户尚未以来启动的应用导航到另一个屏幕。

## <a name="syntax"></a>语法

**回到**([*过渡*])

* *转换*-可选。 若要使用当前屏幕和上一屏幕之间视觉过渡效果。 请参阅本主题前面的此参数的有效值列表。 默认情况下，通过该屏幕将返回的转换是通过其它出现在过渡的反函数。

**Navigate**( *Screen* [, *Transition* [, *UpdateContextRecord* ] ] )

* *Screen* - 必需。 要显示的屏幕。
* *转换*-可选。  切换屏幕时要使用的视觉过渡效果。 请参阅本主题前文中所述此参数的有效值列表。 默认值是**None**。
* *UpdateContextRecord* - 可选。  一条记录，其中包含至少一列的名称以及每列的值。 这一条记录用于更新新屏幕的上下文变量，就像传递到 **[UpdateContext](function-updatecontext.md)** 函数一样。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **导航 （详细信息）** |显示 **Details** 屏幕，没有任何过渡效果，也不会更改上下文变量的值。 |**Details** 屏幕会快速显示。 |
| **Navigate( Details, ScreenTransition.Fade )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。  不更改上下文变量的任何值。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |使用**淡入淡出**过渡效果显示 **Details** 屏幕，并且将 **ID** 上下文变量的值更新为 **12**。 |当前屏幕淡化消失，以显示 **Details** 屏幕，并且将这个屏幕的上下文变量 **ID** 设置为 **12**。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。 将 **ID** 上下文变量的值更新为 **12**，并且将 **Shade** 上下文变量的值更新为 **Color.Red**。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 将 **Details** 屏幕的上下文变量 **ID** 设置为 **12**，并且将上下文变量 **Shade** 设置为 **Color.Red**。 如果将 **Details** 屏幕上某一控件的 **Fill** 属性设置为 **Shade**，则该控件会显示为红色。 |
| **Back()** | 显示与默认返回转换的上一屏幕。 | 显示通过当前屏幕显示通过该转换的反向转换在上一屏幕。 |
| **Back( ScreenTransition.Cover )** |  显示与上一屏幕**涵盖**转换。 | 通过在上一屏幕将显示**涵盖**转换，而不考虑当前屏幕显示通过该转换。 |

### <a name="step-by-step"></a>分步操作

1. 创建一个空白应用程序。

1. 向其添加第二个屏幕。

    应用程序包含两个空白屏幕：**Screen1**并**Screen2**。

1. 设置**填充**的属性**Screen2**的值`Gray`。

1. 上**Screen2**，添加一个按钮，并设置其 **[OnSelect](../controls/properties-core.md)** 属性设为此公式：

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. 在按下**Alt**密钥，请选择该按钮。

    **Screen1**涵盖到左侧的转换通过背景为白色，会显示。

1. 上**Screen1**，添加一个按钮，并设置其**OnSelect**属性设为此公式：

    ```powerapps-dot
    Back()
    ```

1. 在按下**Alt**密钥，请选择该按钮。

    通过转换揭示右侧以灰色背景显示的第二个屏幕 (函数的反函数**涵盖**)。

1. 选择重复来回传递每个屏幕上的按钮。

[其他示例](../add-screen-context-variables.md)
