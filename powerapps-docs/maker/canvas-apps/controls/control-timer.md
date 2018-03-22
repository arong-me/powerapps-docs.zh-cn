---
title: "计时器控件：参考 | Microsoft 文档"
description: "有关计时器控件的信息，包括属性和示例"
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
ms.openlocfilehash: 008c992ad3452c1844064335a51593c222fb1ac1
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="timer-control-in-powerapps"></a>PowerApps 中的计时器控件
一个控件，可确定特定时间后应用的响应方式。

## <a name="description"></a>说明
例如，计时器可确定控件显示的时长，或在经过特定时间后更改控件的其他属性。

请注意，必须先预览应用，然后计时器才能在设计器中运行。  这样一来，用户可以在设计器中配置计时器，不受任何时间限制。

## <a name="key-properties"></a>关键属性
**Duration** – 计时器运行的时长（毫秒计）。  不存在最大值。

**OnTimerEnd** - 计时器运行完毕时应用的响应方式。

**Repeat** - 计时器运行完毕后是否自动重启。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**AutoPause** - 用户导航到另一屏幕时音频或视频剪辑是否自动暂停。

**AutoStart** - 用户导航到包含音频或视频控件的屏幕时，该控件是否自动开始播放剪辑。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

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

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnTimerStart** - 计时器开始运行时应用的响应方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**Start** - 是否播放音频或视频剪辑。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>示例
### <a name="show-a-countdown"></a>显示倒计时
1. 添加一个计时器，并将其命名为 **Countdown**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将计时器的 **Duration** 属性设置为 **10000**，其 **Repeat** 和 **Autostart** 属性设置为 **true**。
3. （可选）通过以下方法可使计时器更易于读取：将其 **[Height](properties-size-location.md)** 属性设置为 **160**，**[Width](properties-size-location.md)** 属性设置为 **600**，并将其 **[Size](properties-text.md)** 属性设置为 **60**。
4. 添加一个标签，然后将其 **[Text](properties-core.md)** 属性设置为以下公式：
   <br>**"Number of seconds remaining: " & RoundUp(10-Countdown.Value/1000, 0)**

    想要了解有关 **[RoundUp](../functions/function-round.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

    标签显示还有多少秒计时器重启。
5. （可选）将计时器的 **[Visible](properties-core.md)** 属性设置为 **false**。

### <a name="animate-a-control"></a>为控件添加动画效果
1. 添加一个计时器，并将其命名为 **FadeIn**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将计时器的 **Duration** 属性设置为 **5000**，其 **Repeat** 和 **Autostart** 属性设置为 **true**。
3. （可选）通过以下方法可使计时器更易于读取：将其 **[Height](properties-size-location.md)** 属性设置为 **160**，**[Width](properties-size-location.md)** 属性设置为 **600**，并将其 **[Size](properties-text.md)** 属性设置为 **60**。
4. 添加一个标签，然后将“[Text](properties-core.md)”属性设置为显示“Welcome!” 并将其 **[Color](properties-color-border.md)** 属性设置为以下公式：
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    想要了解有关 **[ColorFade](../functions/function-colors.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

    标签中的文本渐变为白色，恢复最大亮度，并重复此过程。
5. （可选）将计时器的 **[Visible](properties-core.md)** 属性设置为 **false**。
