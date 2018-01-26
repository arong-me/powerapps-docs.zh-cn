---
title: "下拉列表控件：参考 | Microsoft 文档"
description: "有关下拉列表控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 95e0b5a003586dc028dfe772521a7d8533874c15
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="drop-down-control-in-powerapps"></a>PowerApps 中的下拉列表控件
一个列表，在用户不将其打开的情况下，该表仅显示第一项。

## <a name="description"></a>说明
“下拉列表”控件可以节省屏幕的实际空间，尤其是在列表包含大量选项时。 此控件仅占用一行空间，除非用户选择箭头符号来显示更多选项。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** - 用户更改控件前的初始值。

**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

[!INCLUDE [long-items](../includes/long-items.md)]

Selected - 选定项。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

**ChevronBackground** - 下拉列表中向下箭头的背景色。

**ChevronFill** - 下拉列表中的向下箭头的颜色。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[SelectionColor](properties-color-border.md)** – 所选项目或列表中项目的文本颜色，或笔控件中选择工具的颜色。

**[SelectionFill](properties-color-border.md)** - 所选项目、列表中项目或笔控件选定区域的背景颜色。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例
1. 添加“[按钮](control-button.md)”控件，并将其 **[Text](properties-core.md)** 属性设置为显示 **Collect**。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将此**[按钮](control-button.md)**控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    想要了解有关**[ ClearCollect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
3. 按 F5，单击或点击“**[按钮](control-button.md)**”控件，然后按 Esc。
4. 添加“下拉列表”控件，将其命名为“国家/地区”，并将其 **[Items](properties-core.md)**属性设置为以下公式：
   <br>**Distinct(CityPopulations, Country)**
5. 在垂直方向/纵向添加“文本库”控件，并将其 **[Items](properties-core.md)** 属性设置为以下公式：
   <br>**Filter(CityPopulations, Countries.Selected.Value in Country)**
6. 在“文本库”控件的第一项中，将顶部的“[标签](control-text-box.md)”控件的“[Text](properties-core.md)”属性设置为“ThisItem.City”，然后删除底部的“[标签](control-text-box.md)”控件。
7. 将“文本库”控件的 **[TemplateSize](control-gallery.md)** 属性设置为 **80**。
8. 按 F5，单击或点击“国家/地区”列表中的箭头符号，然后选择该列表中的一个选项。
   
    “文本库”控件仅显示选定国家/地区中的城市。

