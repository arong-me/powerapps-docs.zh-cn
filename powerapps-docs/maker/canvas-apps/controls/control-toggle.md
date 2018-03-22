---
title: 切换控件：参考 | Microsoft 文档
description: 有关切换控件的信息（包括属性和示例）
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
ms.openlocfilehash: dac1f8ea99746f04d2d3305e279a4bc5faf67903
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="toggle-control-in-powerapps"></a>PowerApps 中的切换控件
用户可通过移动其图柄打开或关闭的控件。

## <a name="description"></a>说明
切换设计用于最新的 GUI，但行为方式与复选框相同。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** - 用户更改控件前的初始值。

**[Value](properties-core.md)** - 输入控件的值。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

**FalseFill** - 开关处于关闭状态时的开关填充颜色。

**FalseHoverFill** - 开关处于关闭状态时的开关悬停填充颜色。

**FalseText** - 开关处于关闭状态时显示的文本。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**OnCheck** - 复选框或切换控件的值更改为 **true** 时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnUncheck** - 复选框或切换控件的值更改为 **false** 时应用的响应方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**RailFill** - 切换控件的值为 **false** 时该控件中矩形的背景色，或滑块控件中图柄右侧线条的颜色。

**RailHoverFill** – 将鼠标悬停在切换控件或滑块上时，切换控件（其值为 **false**）中矩形的背景色，或滑块控件中控点右侧线条的颜色。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**ShowLabel** - 是否在开关控件旁边显示文本标签。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**TextPosition** - 标签位于开关控件的左侧还是右侧。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**TrueFill** - 开关处于打开状态时的开关填充颜色。

**TrueHoverFill** - 开关处于打开状态时的开关悬停填充颜色。

**TrueText** - 开关处于打开状态时显示的文本。

**ValueFill** – 切换控件的值为 **true** 时该控件中矩形的背景色，或滑块控件中控点左侧线条的颜色。

**ValueHoverFill** - 将鼠标指针停留在切换控件或滑块上时，切换控件（其值为 **true**）中矩形的背景色，或滑块控件中图柄左侧线条的颜色。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>示例
1. 添加一个切换控件，并将其命名为 **MemberDiscount**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个标签，然后将其 **[Text](properties-core.md)** 属性设置为以下公式：
   <br>**If(MemberDiscount.Value = true, "Price: $75", "Price: $100")**

    想要详细了解 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)吗？
3. 按 F5，并更改 **MemberDiscount** 的值。

    标签显示不同的价格，具体取决于是否已启用 **MemberDiscount**。
4. 若要返回到默认工作区，请按 Esc 键。
