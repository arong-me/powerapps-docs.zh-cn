---
title: 日期选取器控件：参考 | Microsoft 文档
description: 有关日期选取器控件的信息（包括属性和示例）
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
ms.openlocfilehash: f2605680c7b6e8f7102fd3459230344863a93f55
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="date-picker-control-in-powerapps"></a>PowerApps 中的日期选取器控件
用户可单击或点击以指定日期的控件。

## <a name="description"></a>说明
如果添加**日期选取器**控件而非**[文本输入](control-text-input.md)**控件，可帮助确保用户以正确的格式指定日期。

## <a name="key-properties"></a>关键属性
**DefaultDate** - 日期控件的初始值（除非用户更改）。

**SelectedDate** - 日期控件中当前选定的日期。

**Format** - 控件显示日期和用户指定日期所使用的文本格式。 可以将此属性设置为“ShortDate”（默认）或“LongDate”，从而根据此控件的“Language”属性设置日期格式。 若要使用相同的格式，而不考虑语言，也可以将此属性设置为表达式（如“yyyy/mm/dd”）。 例如：

* 如果用户单击或点击 2017 年的最后一天，“Format”属性设置为“ShortDate”，且“Language”属性设置为“en-us”，那么此控件显示“12/31/2017”。
* 如果用户单击或点击 2017 年的最后一天，“Format”属性设置为“LongDate”，且“Language”属性设置为“fr-fr”，那么此控件显示“dimanche 31 decembre 2017”。

**Language** - 确定设置日期格式所使用的语言，包括月份名称。 如果未指定此属性，语言将由用户设备设置决定。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisplayMode](properties-core.md)** – 控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**EndYear** - 用户可将日期选取器控件的值设为的最后一个年份。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** – 控件中的文本与该控件上边缘之间的距离。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**StartYear** - 用户可将日期选取器控件的值设为的最早年份。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
**[Year](../functions/function-datetime-parts.md)**( *DateTimeValue* )

## <a name="example"></a>示例
1. 添加**日期选取器**控件，并将其命名为 **Deadline**。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个“[标签](control-text-box.md)”控件，然后将“[Text](properties-core.md)”属性设置为以下公式：
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**
   
    想要了解有关 **[DateDiff](../functions/function-dateadd-datediff.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
3. 按 F5，在 **Deadline** 中选择一个日期，然后单击或点击“确定”。
   
    此时，“[标签](control-text-box.md)”控件显示今天距离所选日期还剩多少天。
4. 若要返回到默认工作区，请按 Esc 键。
