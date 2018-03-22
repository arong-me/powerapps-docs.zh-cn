---
title: Back 和 Navigate 函数 | Microsoft 文档
description: PowerApps 中 Back 和 Navigate 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/08/2015
ms.author: gregli
ms.openlocfilehash: 58f8c4bf55167e7c891a614a2bfb98ef20dcfd7c
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Microsoft PowerApps 中的 Back 和 Navigate 函数
更改显示的屏幕。

## <a name="overview"></a>概述
大多数应用都包含多个屏幕。  **Back** 和 **Navigate** 函数可用于更改所显示的屏幕。 例如，如果你希望用户在选中某个按钮后显示其他屏幕，请将该按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为一个包含 **Navigate** 函数的公式。 在这个公式中，你可以指定视觉变换效果（比如 **Fade**）来控制屏幕切换方式。  

**Back** 和 **Navigate** 只能更改当前显示的屏幕。 当前未显示的屏幕仍然在后台运行。 你可以构建公式来引用另一个屏幕上控件的属性。 例如，用户可以更改某一个屏幕上滑块的值，导航到在公式中使用这个值的另一个屏幕，看看对新屏幕的显示有何影响。  然后，用户可以导航回原来的屏幕，并且会发现滑块保留了自己的值。

当用户在屏幕之间导航时，[上下文变量](../working-with-variables.md#create-a-context-variable)也会保留。 你可以使用 **Navigate** 设置公式会显示的屏幕的一个或多个上下文变量，这是从屏幕外部设置上下文变量的唯一方法。 这个方法可用于将参数传递到屏幕。 如果你使用过另一款编程工具，就会发现这个方法与将参数传递给过程非常相似。

## <a name="description"></a>说明
### <a name="back"></a>Back
**Back** 函数用于显示最近显示的屏幕。 无需为这个函数指定任何参数。

### <a name="navigate"></a>Navigate
在第一个参数中，指定要显示的屏幕的名称。  

 在第二个参数中，指定旧屏幕切换为新屏幕的方式：

| Transition 参数 | 说明 |
| --- | --- |
| **ScreenTransition.Cover** |新屏幕将滑入视图，盖住当前屏幕。 |
| **ScreenTransition.Fade** |旧屏幕淡出以显示新屏幕。 |
| **ScreenTransition.None** |新屏幕快速替换旧屏幕。 |
| **ScreenTransition.UnCover** |旧屏幕滑出视图，以显示新屏幕。 |

可以使用 **Navigate** 创建或更新的新屏幕的上下文变量。 第三个参数是可选的，它可用于传递一条[记录](../working-with-tables.md#records)，其中包含上下文变量名称（以[列](../working-with-tables.md#columns)名称的形式）和上下文变量的新值。  这条记录就是用于 **[UpdateContext](function-updatecontext.md)** 函数的记录。

设置旧屏幕的 **[OnHidden](../controls/control-screen.md)** 属性和/或新屏幕的 **[OnVisible](../controls/control-screen.md)** 属性，以在过渡期间进行其他更改。 **App.ActiveScreen** 属性将更新以反映更改。

**Back** 通常返回 **true**，但如果当前显示的是第一个屏幕（之前没有显示其他屏幕），则会返回 **false**。  **Navigate** 通常返回 **true**，但如果它的某个参数有问题，则会返回 **false**。

这两个函数只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

## <a name="syntax"></a>语法
**Back**()

**Navigate**( *Screen*, *Transition* [, *UpdateContextRecord* ] )

* *Screen* - 必需。 要显示的屏幕。
* *Transition* - 必需。  切换屏幕时要使用的视觉过渡效果。 请参阅本主题前文中所述此参数的有效值列表。
* *UpdateContextRecord* - 可选。  一条记录，其中包含至少一列的名称以及每列的值。 这一条记录用于更新新屏幕的上下文变量，就像传递到 **[UpdateContext](function-updatecontext.md)** 函数一样。

## <a name="examples"></a>示例
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Navigate( Details, ScreenTransition.None )** |显示 **Details** 屏幕，没有任何过渡效果，也不会更改上下文变量的值。 |**Details** 屏幕会快速显示。 |
| **Navigate( Details, ScreenTransition.Fade )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。  不更改上下文变量的任何值。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |使用**淡入淡出**过渡效果显示 **Details** 屏幕，并且将 **ID** 上下文变量的值更新为 **12**。 |当前屏幕淡化消失，以显示 **Details** 屏幕，并且将这个屏幕的上下文变量 **ID** 设置为 **12**。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |用**淡入淡出**过渡效果显示 **Details** 屏幕。 将 **ID** 上下文变量的值更新为 **12**，并且将 **Shade** 上下文变量的值更新为 **Color.Red**。 |当前屏幕淡化消失，以显示 **Details** 屏幕。 将 **Details** 屏幕的上下文变量 **ID** 设置为 **12**，并且将上下文变量 **Shade** 设置为 **Color.Red**。 如果将 **Details** 屏幕上某一控件的 **Fill** 属性设置为 **Shade**，则该控件会显示为红色。 |

### <a name="step-by-step"></a>分步操作
1. 将默认屏幕命名为 **DefaultScreen**，在其中添加一个标签，并设置这个标签的 **[Text](../controls/properties-core.md)** 属性，使其显示 **Default**。
2. 添加一个屏幕并将其命名为 **AddlScreen**。
3. 为 **AddlScreen** 添加一个标签，并设置标签的 **[Text](../controls/properties-core.md)** 属性，使其显示 **Addl**。
4. 在 **AddlScreen** 上添加一个按钮，将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下函数：<br>**Navigate(DefaultScreen, ScreenTransition.Fade)**
5. 从 **AddlScreen** 中，按 F5，然后选中这个按钮。<br>随即会显示 **DefaultScreen**。

[再举一例](../add-screen-context-variables.md)

