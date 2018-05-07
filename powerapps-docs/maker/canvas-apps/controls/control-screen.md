---
title: 屏幕控件：参考 | Microsoft 文档
description: 有关屏幕控件的信息（包括属性和示例）
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: d03e587d86262bcecf59012e36af0c3dc27b29a3
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="screen-control-in-powerapps"></a>PowerApps 中的屏幕控件
一个包含应用中一个或多个其他控件的 UI 元素。

## <a name="description"></a>描述
大多数应用都有多个“屏幕”控件，其中包含[标签](control-text-box.md)控件、[按钮](control-button.md)控件和其他显示数据和支持导航的控件。

## <a name="key-properties"></a>关键属性
**[BackgroundImage](properties-visual.md)** – 显示在屏幕背景中的图像文件名称。

**[Fill](properties-color-border.md)** – 控件的背景色。

## <a name="additional-properties"></a>其他属性
**[ImagePosition](properties-visual.md)** – 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

OnHidden – 应用在用户离开屏幕时的行为。

OnVisible – 应用在用户转到屏幕时的行为。

OnStart – 用户打开应用时应用的行为。

* 此属性设置为的公式在应用第一屏出现之前运行。 调用 Navigate[](../functions/function-navigate.md) 函数可以更改应用启动时显示的第一屏。
* 无法使用 [UpdateContext](../functions/function-updatecontext.md) 函数设置[上下文变量](../working-with-variables.md)，因为尚未显示任何屏幕。 不过，可以在 Navigate 函数中传递上下文变量，并使用 [Collect](../functions/function-clear-collect-clearcollect.md) 函数创建和填充[集合](../working-with-variables.md)。
* 更新应用后，此属性设置为的公式在 PowerApps Studio 中加载应用时运行。 必须保存、关闭和重新加载应用，才能查看更改此属性产生的影响。
* OnStart 属性实际上是应用（而非屏幕）的属性。 为了方便编辑，请在应用的第一屏上将它作为属性进行查看和修改。 如果删除第一屏或重新排列屏幕，可能会难以查找此属性。 在这种情况下，保存、关闭并重新加载应用，此属性便会作为第一屏的属性重新出现。

## <a name="related-functions"></a>相关函数
[Distinct( DataSource, ColumnName )](../functions/function-distinct.md)

## <a name="example"></a>示例
1. 添加[单选](control-radio.md)控件，将其命名为“ScreenFills”，并将其 [Items](properties-core.md) 属性设置为以下值：<br>
   ["Red", "Green"]
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将默认“屏幕”控件命名为“Source”，添加另一个“屏幕”控件，将其命名为“Target”。
3. 在“Source”中，添加[形状](control-shapes-icons.md)控件（例如箭头），并将其 [OnSelect](properties-core.md) 属性设置为以下公式：<br>
   Navigate(Target, ScreenTransition.Fade)
   
    想要了解有关 [Navigate](../functions/function-navigate.md) 函数或[其他函数](../formula-reference.md)的详细信息？
4. 在“Target”中，添加[形状](control-shapes-icons.md)控件（例如箭头），并将其 [OnSelect](properties-core.md) 属性设置为以下公式：<br>
   Navigate(Source, ScreenTransition.Fade)
5. 将 Target 的 [Fill](properties-color-border.md) 属性设置为以下公式：<br>
   If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))
6. 在“Source”中，按 F5，单击或点击[单选](control-radio.md)控件中的任一选项，然后单击或点击[形状](control-shapes-icons.md)控件。
   
    “Target”显示为所选颜色。
7. 在“Target”上，单击或点击[形状](control-shapes-icons.md)控件以返回“Source”。
8. （可选）单击或点击[单选](control-radio.md)控件中的其他选项，然后单击或点击[形状](control-shapes-icons.md)控件以确认“Target”是否显示为另一种颜色。
9. 若要返回到默认工作区，请按 Esc 键。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
当“屏幕”为文本的有效背景，在以下项之间必须有足够的颜色对比度：
* Fill**[](properties-color-border.md)** 和文本
* BackgroundImage**[](properties-visual.md)** 和文本（如果适用）

例如，如果“屏幕”包含标签**[](control-text-box.md)**，而标签具有透明填充，则屏幕的 Fill**[](properties-color-border.md)** 将有效地成为标签的背景色。

除了文本，请考虑检查与基本图形对象之间的颜色对比度，如“评级”**[](control-rating.md)** 控件中的星级图像。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 必须为每个“屏幕”提供有意义的名称。 可以像其他控件一样查看和编辑屏幕名称：在控件面板的树状视图中，或者在属性窗格的标头中。

    > [!NOTE]
> 加载新“屏幕”时，屏幕阅读器将公布其名称。 
