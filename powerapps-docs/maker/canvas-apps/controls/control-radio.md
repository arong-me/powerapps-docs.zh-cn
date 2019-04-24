---
title: 单选控件：参考 | Microsoft 文档
description: 了解单选控件（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 447cda7a1d8d4f27c8be2b943abd2b5d6b431d49
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61548768"
---
# <a name="radio-control-in-powerapps"></a>PowerApps 中的单选控件

输入控件，显示了多个选项，用户每次可从其中选择一个。

## <a name="description"></a>描述

**单选按钮**控件，标准 HTML 输入控件，在只有少量互斥选项时使用效果最佳。

该控件可有水平或垂直布局。

## <a name="key-properties"></a>关键属性

**[Default](properties-core.md)** - 用户更改前的控件值。

**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

**Layout** - 选项是垂直还是水平布局。

**[Value](properties-core.md)** – 输入控件的值。

## <a name="all-properties"></a>所有属性

**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[DisabledColor](properties-color-border.md)** – 控件的 **[DisplayMode](properties-core.md)** 属性设置为 Disabled**Disabled** 时，该控件中的文本颜色。

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode”**[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)**  – 控件中文本的粗细：**加粗**，**半粗体**，**正常**，或**较浅**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[LineHeight](properties-text.md)** - 文本行之间或列表项之间的距离。

[OnChange](properties-core.md) – 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与此控件的上边缘之间的距离。

[PressedColor](properties-color-border.md) – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

RadioBackgroundFill - 单选按钮控件中的圆圈背景色。

RadioBorderColor - 单选按钮控件中每个选项的圆圈颜色。

RadioSelectionFill - 单选按钮控件中选定选项的圆圈内显示的颜色。

RadioSize - 单选按钮控件中的圆圈直径。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

[Strikethrough](properties-text.md) – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

[Underline](properties-text.md) – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数

[Distinct( DataSource, ColumnName )](../functions/function-distinct.md)

## <a name="example"></a>示例

1. 添加“单选”控件并命名为“Pricing”，然后将其**[“Items”](properties-core.md)** 属性设为以下公式：

    **["Standard", "Premium"]**

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？

2. 添加一个“[标签](control-text-box.md)”控件，将它移到“单选按钮”控件下方，然后将“[标签](control-text-box.md)”控件的“[Text](properties-core.md)”属性设置为以下公式：

    **If("Premium" in Pricing.Selected.Value, "$200 per day", "$150 per day")**

    想要详细了解 [If](../functions/function-if.md) 函数或[其他函数](../formula-reference.md)吗？

3. 按住 Alt 键，同时选择单选按钮控件中的任一选项。

    此时，“[标签](control-text-box.md)”控件会显示所选的相应文本。

4. （可选）按住 Alt 键，选择另一选项以确认相应文本是否会显示。

## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="color-contrast"></a>颜色对比度

除[标准颜色对比度要求](../accessible-apps-color.md)外，还要确保以下内容之间有足够的颜色对比度：

* **RadioSelectionFill** 和 **RadioBackgroundFill**
* **RadioBackgroundFill** 和 **[Fill](properties-color-border.md)**

### <a name="screen-reader-support"></a>屏幕阅读器支持

* 确保每个选项都有**[值](properties-core.md)**。
* 请考虑立即在“单选”控件前添加[标签](control-text-box.md)用作标题。

### <a name="keyboard-support"></a>键盘支持

* 将 **[TabIndex](properties-accessibility.md)** 属性设置为零或更大，以便键盘用户可以导航到它。
* 设置 **[FocusedBorderColor](properties-color-border.md)** 和 **[FocusedBorderThickness](properties-color-border.md)** 属性，使焦点指示器清晰可见。
