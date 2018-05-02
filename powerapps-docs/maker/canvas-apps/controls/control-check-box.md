---
title: 复选框控件：参考 | Microsoft 文档
description: 有关复选框控件的信息，包括属性和示例
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 9b51e1cf59c5df163027e8768c21d6ae544d7ba1
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="check-box-control-in-powerapps"></a>PowerApps 中的复选框控件
用户可选择或清除以将其值设置为 **true** 或 **false** 的控件。

## <a name="description"></a>说明
用户可以使用此熟悉的控件指定布尔值，这个控件在 GUI 中已经使用了数十年。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** - 用户更改控件前的初始值。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

**[Value](properties-core.md)** – 输入控件的值。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**CheckboxBackgroundFill** - 复选框控件中围绕选中标记的框的背景颜色。

**CheckboxBorderColor** - 复选框控件中围绕选中标记的边框颜色。

**CheckboxSize** - 复选框控件中围绕选中标记的框的宽度和高度。

**CheckmarkFill** - 复选框控件中选中标记的颜色。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**OnCheck** - 复选框或切换控件的值更改为 **true** 时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnUncheck** - 复选框或切换控件的值更改为 **false** 时应用的响应方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[VerticalAlign](properties-text.md)** – 控件上的文本相对于该控件垂直居中的位置。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>示例
1. 添加**复选框**控件，将其命名为 **chkReserve**，然后设置其 [Text](properties-core.md) 属性，使其显示为“暂时保留”。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加[日期选取器](control-date-picker.md)控件，将其 [Visible](properties-core.md) 属性设置为此公式：
   <br>**If(chkReserve.Value = true, true)**
   
    想要详细了解 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)吗？
3. 按 F5，单击或点击“chkReserve”，将其“[Value](properties-core.md)”属性设置为 **true**，然后再次单击或点击“chkReserve”，将其“[Value](properties-core.md)”属性设置为 **false**。
   
    如果 **chkReserve** 的 [Value](properties-core.md) 属性为 **true**，则将显示“[日期选取器](control-date-picker.md)”控件，如果为 **false**，则不会显示。
4. 若要返回到默认工作区，请按 Esc 键。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* CheckmarkFill 和 CheckboxBackgroundFill
* CheckboxBackgroundFill 和 Fill**[](properties-color-border.md)**
* CheckboxBackgroundFill 和 PressedFill**[](properties-color-border.md)**
* CheckboxBackgroundFill 和 HoverFill**[](properties-color-border.md)**

这是除标准颜色对比度以外的要求。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* “Text”**[](properties-core.md)** 必须存在。

### <a name="keyboard-support"></a>键盘支持
* “TabIndex”**[](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用“FocusedBorderColor”**[](properties-color-border.md)** 和“FocusedBorderThickness**[](properties-color-border.md)**”来实现此目的。
 