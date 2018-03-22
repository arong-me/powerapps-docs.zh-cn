---
title: 文本输入控件：参考 | Microsoft 文档
description: 有关文本输入控件的信息（包括属性和示例）
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
ms.openlocfilehash: 4082034d843765025bb6e40cab83705582417d51
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="text-input-control-in-powerapps"></a>PowerApps 中的文本输入控件
用户可在其中键入文本、数字和其他数据的框。

## <a name="description"></a>说明
用户可通过将数据键入文本输入控件来进行指定。 根据配置应用的方式，该数据可能会被添加到某个数据源、用于计算临时值或以其他某种方式合并。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** - 用户更改控件前的初始值。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

**Clear** - 文本输入控件是否显示“X”，用户可点击或单击该符号以清除该控件的内容。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**DelayOutput** - 如果设置为 true，用户输入会延迟半秒后注册。  可帮助延迟成本高昂的操作，直到用户完成输入文本（例如，输入用在其他公式中时有益于筛选）。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**Format** – 用户输入是仅在数量上进行限制，还是限制所有文本。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**HintText** - 输入文本控件为空时其中显示的浅灰色文本。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[LineHeight](properties-text.md)** – 诸如文本行之间或列表中各项之间的距离。

**MaxLength** - 用户可键入文本输入控件中的字符数。

**Mode** - 控件处于 **SingleLine**、**MultiLine** 或 **Password** 模式。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[RadiusBottomLeft](properties-size-location.md)** – 控件左下角圆角的程度。

**[RadiusBottomRight](properties-size-location.md)** – 控件右下角圆角的程度。

**[RadiusTopLeft](properties-size-location.md)** – 控件左上角圆角的程度。

**[RadiusTopRight](properties-size-location.md)** – 控件右上角圆角的程度。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**DateTimeValue**( *String* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>示例
### <a name="collect-data"></a>收集数据
1. 添加两个文本输入控件，并将它们命名为 **inputFirst** 和 **inputLast**。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个按钮，将其 **[Text](properties-core.md)** 属性设置为 **Add**，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
3. 以纵向/垂直方向添加文本库，将其 **[Items](properties-core.md)** 属性设置为 **Names**，并将 **Subtitle1** 的 **[Text](properties-core.md)** 属性设置为 **ThisItem.FirstName**。
4. （可选）在模板库中，删除底部的“Body1”标签，然后将库的“[TemplateSize](control-gallery.md)”属性设置为“80”。
5. 按 F5，将一个文本字符串键入 **inputFirst** 和 **inputLast**，然后单击或点击“添加”按钮。
6. （可选）向集合添加更多名称，然后按 Esc 返回到默认工作区。

### <a name="prompt-for-a-password"></a>提示输入密码
1. 添加文本输入控件，将其命名为 **inputPassword**，并将其 **Mode** 属性设置为 **Password**。
2. 添加一个标签，然后将其 **[Text](properties-core.md)** 属性设置为以下公式：<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**
   
    想要详细了解 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)吗？
3. 按 F5，然后在 **inputPassword** 中键入 **P@ssw0rd**。
   
    密码键入完毕后，标签不再显示“拒绝访问”，而会显示“已授予访问权限”。
4. 若要返回到默认工作区，请按 Esc 键。
5. （可选）添加一个控件（如箭头），配置它以导航到另一个屏幕，且仅在用户键入密码后才显示。
6. （可选）添加一个按钮，配置其 **[Text](properties-core.md)** 属性，使其显示**登录**，添加一个计时器，如果用户键入错误的密码，则禁用输入文本控件一段时间，然后单击或点击“登录”按钮。

