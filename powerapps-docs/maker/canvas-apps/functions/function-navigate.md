---
title: Back 和 Navigate 函数 | Microsoft 文档
description: PowerApps 中 Back 和 Navigate 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8f63321b128214d14cd2f4e521d7cc1b85c7b98f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984478"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Microsoft PowerApps 中的 Back 和 Navigate 函数

更改显示的屏幕。

## <a name="overview"></a>概述

大多数应用都包含多个屏幕。  **Back** 和 **Navigate** 函数可用于更改所显示的屏幕。 例如，如果你希望用户在选中某个按钮后显示其他屏幕，请将该按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为一个包含 **Navigate** 函数的公式。 在这个公式中，你可以指定视觉变换效果（比如 **Fade**）来控制屏幕切换方式。  

**Back** 和 **Navigate** 只能更改当前显示的屏幕。 当前未显示的屏幕仍然在后台运行。 您可以生成引用其他屏幕上控件属性的公式。 例如，用户可以在一个屏幕上更改滑块的值，导航到在公式中使用该值的不同屏幕，并确定它如何影响新屏幕中发生的情况。 然后，用户可以导航回原始屏幕并确认滑块已保留其值。

当用户在屏幕之间导航时，[上下文变量](../working-with-variables.md#use-a-context-variable)也会保留。 你可以使用 **Navigate** 设置公式会显示的屏幕的一个或多个上下文变量，这是从屏幕外部设置上下文变量的唯一方法。 这个方法可用于将参数传递到屏幕。 如果你使用过另一款编程工具，就会发现这个方法与将参数传递给过程非常相似。

只能在[行为公式](../working-with-formulas-in-depth.md)中使用这两种函数。

## <a name="navigate"></a>Navigate

在第一个参数中，指定要显示的屏幕的名称。  

 在第二个参数中，指定旧屏幕切换为新屏幕的方式：

| Transition 参数 | 描述 | 便于 |
| --- | --- | --- |
| **ScreenTransition.Cover** |新屏幕将向右移动，以覆盖当前屏幕。 | ![屏幕过渡覆盖动画](media/function-navigate/cover.gif) |
| **Screentransition.none. CoverRight** |新屏幕将滑入视图，从左到右移动以覆盖当前屏幕。 | ![屏幕过渡向右动画显示](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |当前屏幕淡化消失，以显示新屏幕。 | ![屏幕过渡淡化动画](media/function-navigate/fade.gif) |
| **Screentransition.none** （默认值） |新屏幕会迅速替换当前屏幕。 | ![屏幕过渡无动画](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | 当前屏幕滑出视图，从右到左移动以显示新屏幕。 | ![屏幕转换发现动画](media/function-navigate/uncover.gif) |
| **Screentransition.none. UnCoverRight** | 当前屏幕从视图中滑出，并向右移动以显示新屏幕。 | ![屏幕过渡向右发现动画](media/function-navigate/uncoverright.gif) |

可以使用 **Navigate** 创建或更新的新屏幕的上下文变量。 第三个参数是可选的，它可用于传递一条[记录](../working-with-tables.md#records)，其中包含上下文变量名称（以[列](../working-with-tables.md#columns)名称的形式）和上下文变量的新值。  这条记录就是用于 **[UpdateContext](function-updatecontext.md)** 函数的记录。

设置旧屏幕的 **[OnHidden](../controls/control-screen.md)** 属性和/或新屏幕的 **[OnVisible](../controls/control-screen.md)** 属性，以在过渡期间进行其他更改。 **App.ActiveScreen** 属性将更新以反映更改。

通常，**导航**返回**true** ，但如果遇到错误，则返回**false** 。

## <a name="back"></a>Back

**Back**函数返回到最近显示的屏幕。

对于每个**导航**调用，应用将跟踪显示的屏幕和转换。 您可以使用连续的**回**拨调用，使其返回到用户启动应用程序时显示的屏幕。

当**Back**函数运行时，将默认使用反向转换。 例如，如果屏幕通过**CoverRight**过渡出现，则**Back**使用 "**揭开**" （左侧）进行返回。  **淡化**和**None**都是自己的逆。 向**后**传递可选参数以强制执行特定转换。

**Back**通常返回**true** ，但如果用户从启动应用后未导航到其他屏幕，则返回**false** 。

## <a name="syntax"></a>语法

**后退**（[*转换*]）

* *转换*-可选。 要在当前屏幕和上一屏幕之间使用的视觉转换。 请参阅本主题前面的此参数的有效值列表。 默认情况下，屏幕返回的转换是它所显示的转换的反向转换。

**导航**（ *Screen* [，*过渡*[， *UpdateContextRecord* ]]）

* *Screen* - 必需。 要显示的屏幕。
* *转换*-可选。  切换屏幕时要使用的视觉过渡效果。 请参阅本主题前文中所述此参数的有效值列表。 默认值为 "**无**"。
* *UpdateContextRecord* - 可选。  一条记录，其中包含至少一列的名称以及每列的值。 这一条记录用于更新新屏幕的上下文变量，就像传递到 **[UpdateContext](function-updatecontext.md)** 函数一样。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **导航（详细信息）** |显示 **Details** 屏幕，没有任何过渡效果，也不会更改上下文变量的值。 |**Details** 屏幕会快速显示。 |
| **Navigate( Details, ScreenTransition.Fade )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。  不更改上下文变量的任何值。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |使用**淡入淡出**过渡效果显示 **Details** 屏幕，并且将 **ID** 上下文变量的值更新为 **12**。 |当前屏幕淡化消失，以显示 **Details** 屏幕，并且将这个屏幕的上下文变量 **ID** 设置为 **12**。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。 将 **ID** 上下文变量的值更新为 **12**，并且将 **Shade** 上下文变量的值更新为 **Color.Red**。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 将 **Details** 屏幕的上下文变量 **ID** 设置为 **12**，并且将上下文变量 **Shade** 设置为 **Color.Red**。 如果将 **Details** 屏幕上某一控件的 **Fill** 属性设置为 **Shade**，则该控件会显示为红色。 |
| **Back()** | 显示具有默认返回转换的上一个屏幕。 | 通过当前屏幕显示的过渡的反向转换显示上一屏幕。 |
| **Back （Screentransition.none）** |  显示带有**封面**转换的上一个屏幕。 | 无论当前屏幕出现哪种过渡，都将通过**封面**转换显示上一屏幕。 |

### <a name="step-by-step"></a>分步操作

1. 创建空白应用。

1. 向其中添加另一个屏幕。

    应用包含两个空白屏幕：**Screen1**和**Screen2**。

1. 将**Screen2**的**Fill**属性设置为 `Gray` 的值。

1. 在**Screen2**上，添加一个按钮，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. 按下**Alt**键的同时，选择按钮。

    **Screen1**将显示一个白色背景，通过左侧的转换。

1. 在**Screen1**上，添加一个按钮，并将其**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Back()
    ```

1. 按下**Alt**键的同时，选择按钮。

    第二个屏幕显示为灰色背景，通过向右露出的过渡（反转**覆盖**）。

1. 重复选择每个屏幕上的按钮，以便来回弹跳。

[其他示例](../add-screen-context-variables.md)
