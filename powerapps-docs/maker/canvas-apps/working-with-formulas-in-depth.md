---
title: 了解行为公式 | Microsoft 文档
description: 有关使用行为公式的参考信息
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/10/2015
ms.author: gregli
ms.openlocfilehash: 8ac9cfc2a949cf059d84b5338220e0366094e24b
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015584"
---
# <a name="understand-behavior-formulas-in-powerapps"></a>了解 PowerApps 中的行为公式

大多数公式都是用来计算值的。  就像 Excel 电子表格一样，当值发生更改时，会自动执行重新计算。  例如，可能希望在“[标签](controls/control-text-box.md)”控件中用红色显示小于零的值，用黑色显示大于等于零的值。 所以，可以将这个控件的**[颜色](controls/properties-color-border.md)** 属性设置为以下公式：
<br>**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

对于这一点，如果用户选择**[按钮](controls/control-button.md)** 控件，会发生什么情况？  不会更改任何值，所有没有任何新值需要计算。 Excel 没有类似**[按钮](controls/control-button.md)** 这样的控件。  

通过选择**[按钮](controls/control-button.md)** 控件，用户会发起一系列操作或行为，从而更改应用的状态：

* 更改显示的屏幕：**[Back](functions/function-navigate.md)** 和 **[Navigate](functions/function-navigate.md)** 函数。
* 控制[信号](functions/signals.md)：**[Enable](functions/function-enable-disable.md)** 和 **[Disable](functions/function-enable-disable.md)** 函数。
* 刷新、更新或删除[数据源](working-with-data-sources.md)中的项目：**[Refresh](functions/function-refresh.md)**、**[Update](functions/function-update-updateif.md)**、**[UpdateIf](functions/function-update-updateif.md)**、**[Patch](functions/function-patch.md)**、**[Remove](functions/function-remove-removeif.md)**、**[RemoveIf](functions/function-remove-removeif.md)** 函数。
* 更新[上下文变量](working-with-variables.md#create-a-context-variable)：**[UpdateContext](functions/function-updatecontext.md)** 函数。
* 创建、更新或删除[集合](working-with-data-sources.md#collections)中的项：**[Collect](functions/function-clear-collect-clearcollect.md)**、**[Clear](functions/function-clear-collect-clearcollect.md)**、**[ClearCollect](functions/function-clear-collect-clearcollect.md)** 函数。

由于这些函数可更改应用的状态，因此无法自动重新计算。 你可以在 **[OnSelect](controls/properties-core.md)**、**[OnVisible](controls/control-screen.md)**、**[OnHidden](controls/control-screen.md)** 和其他 **On...** 属性的公式（称为行为公式）中使用这些函数。

### <a name="more-than-one-action"></a>多个操作
使用分号可创建要执行的操作列表。 例如，你可能希望更新上下文变量，然后返回到上一个屏幕：

* **UpdateContext( { x: 1 } ); Back()**

操作按照它们在公式中出现的顺序执行。  当前函数完成执行后，才会开始执行下一个函数。 如果发生错误，则可能无法继续执行后续函数。

