---
title: 屏幕控件：参考 | Microsoft 文档
description: 有关屏幕控件的信息（包括属性和示例）
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1b9f819ab7e047b68e60b9c78e6f7f000502abb8
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993316"
---
# <a name="screen-control-in-powerapps"></a>PowerApps 中的屏幕控件

一个包含应用中一个或多个其他控件的 UI 元素。

## <a name="description"></a>描述

大多数应用都有多个“屏幕”控件，其中包含[标签](control-text-box.md)控件、[按钮](control-button.md)控件和其他显示数据和支持导航的控件。 有关如何添加屏幕、对屏幕重新排序和配置导航的信息，请查看[添加屏幕](../add-screen-context-variables.md)。

## <a name="key-properties"></a>关键属性

**[BackgroundImage](properties-visual.md)** – 显示在屏幕背景中的图像文件名称。

**[Fill](properties-color-border.md)** – 控件的背景色。

## <a name="additional-properties"></a>其他属性

**Height** -屏幕的高度。 如果应用有响应（"[**缩放到合适**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation)" 处于**关闭状态**），并且运行该应用的设备小于此属性，则屏幕可以垂直滚动。

**[ImagePosition](properties-visual.md)** – 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

**名称**-屏幕的名称。

OnHidden – 应用在用户离开屏幕时的行为。

OnVisible – 应用在用户转到屏幕时的行为。  使用此属性设置变量并预先加载屏幕使用的数据。  在应用程序启动时，使用[**app.config**](../functions/object-app.md#onstart-property)属性进行设置。

**方向**-屏幕的方向。 如果其**宽度**大于其**高度**，则方向将是**Layout。水平**;否则，它将为**垂直布局**。

**大小**-用于对屏幕大小进行分类的正整数。 通过将屏幕的**Width**属性与[**SizeBreakpoints**](../functions/signals.md)属性中的值进行比较来确定分类。 **ScreenSize**类型由四个值（**小**、**中**、**大**和**超大型**）组成，它们对应于整数1到4。

**Width** -屏幕的宽度。 如果应用有响应（"[**缩放到合适**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation)" 处于**关闭状态**），并且运行该应用的设备比此属性窄，则屏幕可以水平滚动。

## <a name="related-functions"></a>相关函数

[Distinct( DataSource, ColumnName )](../functions/function-distinct.md)

## <a name="example"></a>示例

1. 添加[单选](control-radio.md)控件，将其命名为“ScreenFills”，并将其 [Items](properties-core.md) 属性设置为以下值：

    `["Red", "Green"]`

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？

1. 将默认“屏幕”控件命名为“Source”，添加另一个“屏幕”控件，将其命名为“Target”。

1. 在 "**源**" 中，添加 **[形状](control-shapes-icons.md)** 控件（例如箭头），并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：

    `Navigate(Target, ScreenTransition.Fade)`

    想要了解有关 [Navigate](../functions/function-navigate.md) 函数或[其他函数](../formula-reference.md)的详细信息？

1. 在“Target”中，添加[形状](control-shapes-icons.md)控件（例如箭头），并将其 [OnSelect](properties-core.md) 属性设置为以下公式：

    `Navigate(Source, ScreenTransition.Fade)`

1. 将 Target 的 [Fill](properties-color-border.md) 属性设置为以下公式：

    `If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))`

1. 选择**源**屏幕，然后在按住 Alt 键的同时选择 **[单选](control-radio.md)** 控件中的任一选项，然后选择 **[形状](control-shapes-icons.md)** 控件。

    **目标**显示为您选择的颜色。

1. 在 "**目标**" 中，选择要返回到**源**的 **[形状](control-shapes-icons.md)** 控件。

1. 可有可无选择 " **[收音机](control-radio.md)** " 控件中的 "其他" 选项，然后选择 **[形状](control-shapes-icons.md)** 控件以确认**目标**以其他颜色显示。

1. 可有可无通过将鼠标悬停在左侧导航栏中的 "**目标**" 上方，选择显示的省略号，然后选择 "**上移**"，对屏幕重新排序。

    当用户打开应用时，将首先出现**目标**。

## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="color-contrast"></a>颜色对比度

当“屏幕”为文本的有效背景，在以下项之间必须有足够的颜色对比度：

- **[Fill](properties-color-border.md)** 和文本
- **[BackgroundImage](properties-visual.md)** 和文本（如果适用）

例如，如果“屏幕”包含 **[标签](control-text-box.md)** ，而标签具有透明填充，则屏幕的 **[Fill](properties-color-border.md)** 将有效地成为标签的背景色。

除了文本，请考虑检查与基本图形对象之间的颜色对比度，如 **[“评级”](control-rating.md)** 控件中的星级图像。

### <a name="screen-reader-support"></a>屏幕阅读器支持

- 必须为每个“屏幕”提供有意义的名称。 可以像其他控件一样查看和编辑屏幕名称：在控件面板的树状视图中，或者在属性窗格的标头中。

    > [!NOTE]
  > 加载新“屏幕”时，屏幕阅读器将公布其名称。
