---
title: 计时器控件：参考 | Microsoft 文档
description: 有关计时器控件的信息，包括属性和示例
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 934ab9bddfb429ae3ed96706420af002a87697fb
ms.sourcegitcommit: 87122dba00b4177ef736d87ecdde79581649ba42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44499513"
---
# <a name="timer-control-in-powerapps"></a>PowerApps 中的计时器控件
一个控件，可确定特定时间后应用的响应方式。

## <a name="description"></a>描述
例如，计时器可确定控件显示的时长，或在经过特定时间后更改控件的其他属性。

请注意，必须先预览应用，然后计时器才能在设计器中运行。  这样一来，用户可以在设计器中配置计时器，不受任何时间限制。

## <a name="key-properties"></a>关键属性
**Duration** – 计时器运行的时长（毫秒计）。  不存在最大值。

**OnTimerEnd** - 计时器运行完毕时应用的响应方式。

**Repeat** - 计时器运行完毕后是否自动重启。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**AutoPause** – 用户导航到其他屏幕时计时器控件是否自动暂停。

**AutoStart** – 用户导航到包含计时器控件的屏幕时，该控件是否自动开始播放。

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

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnTimerStart** - 计时器开始运行时应用的响应方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

[Reset](properties-core.md) – 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**Start** – 是否启动计时器。

[Strikethrough](properties-text.md) – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

[Underline](properties-text.md) – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

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

### <a name="animate-a-control"></a>为控件添加动画效果
1. 添加一个计时器，并将其命名为 **FadeIn**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将计时器的 **“Duration”** 属性设置为 **“5000”**，将其 **“Repeat”** 属性设置为 **“true”**，并将其 **[“Text”](properties-core.md)** 属性设置为“切换动画”。
3. （可选）通过以下方法可使计时器更易于读取：将其 **[Height](properties-size-location.md)** 属性设置为 **160**，**[Width](properties-size-location.md)** 属性设置为 **600**，并将其 **[Size](properties-text.md)** 属性设置为 **60**。
4. 添加一个标签，然后将“[Text](properties-core.md)”属性设置为显示“Welcome!” 并将其 **[Color](properties-color-border.md)** 属性设置为以下公式：
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    想要了解有关 **[ColorFade](../functions/function-colors.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

5. 选择计时器按钮以启动或停止动画。 标签中的文本渐变为白色，恢复最大亮度，并重复此过程。


## <a name="accessibility-guidelines"></a>辅助功能准则
**[适用按钮](control-button.md)** 的相同准则，因为“计时器”是专用按钮。

> [!IMPORTANT]
> 在没有直接用户干预的情况下控制计时器不支持辅助功能。 例如，可以通过在计时器上方放置其他控件或将其**[“Visible”](properties-core.md)** 属性设置为“false”从视觉上隐藏计时器。 显示屏幕时计时器会自动启动，并在一段时间后自动执行一些操作。 目前，没有任何通用的方法可以使该情况支持辅助功能。

其他辅助功能准则如下所示。

### <a name="timing"></a>执行时间
如果计时器启动或停止自动，考虑用户是否有足够的时间来阅读和使用内容。 键盘和屏幕阅读器用户可能需要更多的时间来响应定时事件。

这些任何一项策略均足以：
* 允许用户取消定时事件
* 允许用户在开始之前调整时间限制
* 在时间限制到期前 20 秒发出警告，并提供一种轻松扩展限制的方法

某些情况不受这些要求的限制。 请参阅[有关时间限制的 WCAG 2.0 准则](https://www.w3.org/TR/WCAG20/#time-limits)了解详细信息。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“Text”](properties-core.md)** 必须存在。
* 不要对时间敏感型和重要信息使用**[“Text”](properties-core.md)**。 屏幕阅读器用户不会收到有关**[“Text”](properties-core.md)** 更改的通知。

    > [!NOTE]
  > 屏幕阅读器将每隔 5 秒公告一次运行时间。 但是，计时器 **[Text](properties-core.md)** 不会包含在公告中。

* 请考虑添加 **[Label](control-text-box.md)** 以显示运行时间。 使用计时器的 **[Text](properties-core.md)** 以指示用户启动或停止计时器。
