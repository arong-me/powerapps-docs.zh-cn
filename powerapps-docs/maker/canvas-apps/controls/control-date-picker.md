---
title: 日期选取器控件：参考 | Microsoft 文档
description: 有关日期选取器控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/10/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4d241eb8ce8ec9f6d0fa17ac802aeddbd142de25
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223348"
---
# <a name="date-picker-control-in-power-apps"></a>Power Apps 中的日期选取器控件
用户可单击或点击以指定日期的控件。

## <a name="description"></a>说明
如果添加**日期选取器**控件而非 **[文本输入](control-text-input.md)** 控件，可帮助确保用户以正确的格式指定日期。

## <a name="key-properties"></a>关键属性
**DefaultDate** - 日期控件的初始值（除非用户更改）。

**SelectedDate** - 日期控件中当前选定的日期。  此日期以本地时间表示。

**Format** - 控件显示日期和用户指定日期所使用的文本格式。 可以将此属性设置为“ShortDate”（默认）或“LongDate”，从而根据此控件的“Language”属性设置日期格式。 若要使用相同的格式，而不考虑语言，也可以将此属性设置为表达式（如“yyyy/mm/dd”）。 例如：

* 如果用户单击或点击 2017 年的最后一天，“Format”属性设置为“ShortDate”，且“Language”属性设置为“en-us”，那么此控件显示“12/31/2017”。
* 如果用户单击或点击 2017 年的最后一天，“Format”属性设置为“LongDate”，且“Language”属性设置为“fr-fr”，那么此控件显示“dimanche 31 decembre 2017”。

**Language** –确定用于设置日期格式的语言，包括月份的名称。 如果未指定此属性，语言将由用户设备设置决定。 支持的值包括 "EN-US" 和 "FR"。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**DateTimeZone** –是以**UTC**还是以用户的**本地**时间显示日期。

**[DisplayMode](properties-core.md)** – 控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md)属性设置为 Disabled 时，该控件边框的颜色。

**[DisabledColor](properties-color-border.md)** – 控件的 **[DisplayMode](properties-core.md)** 属性设置为 Disabled**Disabled** 时，该控件中的文本颜色。

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode” **[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**EndYear** - 用户可将日期选取器控件的值设为的最后一个年份。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** - 控件中文本的粗细：粗体、半粗体、一般或较细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**IconFill** - 日期选取器图标的前景色。

**IconBackground** - 日期选取器图标的背景色。

**InputTextPlaceholder** –未输入日期时显示的说明文本。

**IsEditable** -是否可以编辑 datepicker 文本。 如果为 false，则仅可使用日历更改日期。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[OnChange](properties-core.md)** -用户更改控件的值时应用的响应方式。 

**OnChange**和**OnSelect**之间的差异：如果用户*单击*导致更改，则在相同用户操作上 OnSelect 和 OnChange 触发器。 在这种情况下，OnSelect 将在 OnChange**之前**触发。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** – 控件中的文本与该控件的上边缘之间的距离。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**StartOfWeek** -要在日期选取器控件的第一天列中显示的一周中的某一天。

**StartYear** - 用户可将日期选取器控件的值设为的最早年份。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
**[Year](../functions/function-datetime-parts.md)** ( *DateTimeValue* )

## <a name="example"></a>示例
1. 添加**日期选取器**控件，并将其命名为 **Deadline**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个“[标签](control-text-box.md)”控件，然后将“[Text](properties-core.md)”属性设置为以下公式：
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**

    想要了解有关 **[DateDiff](../functions/function-dateadd-datediff.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
3. 按 F5，在 **Deadline** 中选择一个日期，然后单击或点击“确定”。

    此时，“[标签](control-text-box.md)”控件显示今天距离所选日期还剩多少天。
4. 若要返回到默认工作区，请按 Esc 键。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
* 适用[标准颜色对比度要求](../accessible-apps-color.md)。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* [“AccessibleLabel”](properties-accessibility.md)必须存在。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。

> [!TIP]
> 当日历打开时，按**page up**和**page down**可在月之间导航，并按**shift + page Up** ，按**shift + page down**可在年份之间导航。
