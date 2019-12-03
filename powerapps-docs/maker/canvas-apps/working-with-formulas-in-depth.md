---
title: 了解画布应用中的行为公式 | Microsoft Docs
description: 有关使用行为公式的参考信息，这些公式在 Power Apps 中更改 canvas 应用的状态
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3402931e6a20fffb68ac9af37f62a2372afc5f57
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732248"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-power-apps"></a>了解 Power Apps 中的画布应用的行为公式

大多数公式都是用来计算值的。  就像 Excel 电子表格一样，当值发生更改时，会自动执行重新计算。  例如，可能希望在“[标签](controls/control-text-box.md)”控件中用红色显示小于零的值，用黑色显示大于等于零的值。 所以，可以将这个控件的 **[颜色](controls/properties-color-border.md)** 属性设置为以下公式：

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

对于这一点，如果用户选择 **[按钮](controls/control-button.md)** 控件，会发生什么情况？  不会更改任何值，所有没有任何新值需要计算。 Excel 没有类似 **[按钮](controls/control-button.md)** 这样的控件。  

通过选择 **[按钮](controls/control-button.md)** 控件，用户会发起一系列操作或行为，从而更改应用的状态：

* 更改显示的屏幕： **[Back](functions/function-navigate.md)** 和 **[Navigate](functions/function-navigate.md)** 函数。
* 控制[信号](functions/signals.md)： **[Enable](functions/function-enable-disable.md)** 和 **[Disable](functions/function-enable-disable.md)** 函数。
* 刷新、更新或删除[数据源](working-with-data-sources.md)中的项目： **[Refresh](functions/function-refresh.md)** 、 **[Update](functions/function-update-updateif.md)** 、 **[UpdateIf](functions/function-update-updateif.md)** 、 **[Patch](functions/function-patch.md)** 、 **[Remove](functions/function-remove-removeif.md)** 、 **[RemoveIf](functions/function-remove-removeif.md)** 函数。
* 更新[上下文变量](working-with-variables.md#use-a-context-variable)： **[UpdateContext](functions/function-updatecontext.md)** 函数。
* 创建、更新或删除[集合](working-with-data-sources.md#collections)中的项： **[Collect](functions/function-clear-collect-clearcollect.md)** 、 **[Clear](functions/function-clear-collect-clearcollect.md)** 、 **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 函数。

由于这些函数可更改应用的状态，因此无法自动重新计算。 你可以在 **[OnSelect](controls/properties-core.md)** 、 **[OnVisible](controls/control-screen.md)** 、 **[OnHidden](controls/control-screen.md)** 和其他 **On...** 属性的公式（称为行为公式）中使用这些函数。

### <a name="more-than-one-action"></a>多个操作
使用分号可创建要执行的操作列表。 例如，你可能希望更新上下文变量，然后返回到上一个屏幕：

* **UpdateContext( { x: 1 } ); Back()**

操作按照它们在公式中出现的顺序执行。  当前函数完成执行后，才会开始执行下一个函数。 如果发生错误，则可能无法继续执行后续函数。

