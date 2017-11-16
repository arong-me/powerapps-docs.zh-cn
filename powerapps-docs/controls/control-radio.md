---
title: "单选控件：参考 | Microsoft 文档"
description: "了解单选控件（包括属性和示例）"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: c8eab64efa3ad4487c129cec9be7f12147d3ca8d
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="radio-control-in-powerapps"></a>PowerApps 中的单选控件
显示所有选项的列表，但用户只能一次选择一个选项。

## <a name="description"></a>说明
用户有几十年使用经验的“单选”控件最好只与几个互斥选项一同使用。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** – 用户更改控件前的初始值。

**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

[!INCLUDE [long-items](../../includes/long-items.md)]

**[Value](properties-core.md)** - 输入控件的值。

## <a name="all-properties"></a>所有属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** - 控件具有键盘焦点时，该控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[LineHeight](properties-text.md)** - 文本行之间或列表项之间的距离。

**[OnChange](properties-core.md)** – 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** - 控件中的文本与该控件的下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与此控件的上边缘之间的距离。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

RadioBackgroundFill - 单选按钮控件中的圆圈背景色。

RadioBorderColor - 单选按钮控件中每个选项的圆圈颜色。

RadioSelectionFill - 单选按钮控件中选定选项的圆圈内显示的颜色。

RadioSize - 单选按钮控件中的圆圈直径。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>示例
1. 添加“单选”控件并命名为“Pricing”，然后将其**[“Items”](properties-core.md)**属性设为以下公式：
   <br>**["Standard", "Premium"]**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个“[标签](control-text-box.md)”控件，将它移到“单选按钮”控件下方，然后将“[标签](control-text-box.md)”控件的“[Text](properties-core.md)”属性设置为以下公式：
   <br>**If("Premium" in Pricing.Selected.Value, "$200 per day", "$150 per day")**
   
    想要详细了解 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)吗？
3. 按 F5 键，然后选中“单选”控件中的任一选项。
   
    此时，“[标签](control-text-box.md)”控件会显示所选的相应文本。
4. （可选）选中“单选”控件中的另一选项，以确认相应文本是否会显示。
5. 若要返回到默认工作区，请按 Esc 键。
