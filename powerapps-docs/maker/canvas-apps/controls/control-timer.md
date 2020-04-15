---
title: 计时器控件：参考 | Microsoft 文档
description: 有关计时器控件的信息，包括属性和示例
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88c96535de5fc4f77da06ca11ba3f6c49b37bcdd
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385226"
---
# <a name="timer-control-in-power-apps"></a>Power Apps 中的计时器控制
一个控件，可确定特定时间后应用的响应方式。

## <a name="description"></a>说明
例如，计时器可确定控件显示的时长，或在经过特定时间后更改控件的其他属性。

> [!NOTE]
> 在 Power Apps Studio 中，计时器仅在预览模式下运行。


## <a name="key-properties"></a>关键属性
**Duration** – 计时器运行的时长（毫秒计）。 最大值为24小时（以毫秒表示）。 默认值为60秒。

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

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode” **[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** - 控件中文本的粗细：粗体、半粗体、一般或较细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

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
3. （可选）通过以下方法可使计时器更易于读取：将其 **[Height](properties-size-location.md)** 属性设置为 **160**， **[Width](properties-size-location.md)** 属性设置为 **600**，并将其 **[Size](properties-text.md)** 属性设置为 **60**。
4. 添加一个标签，然后将其 **[Text](properties-core.md)** 属性设置为以下公式：
   <br>**"Number of seconds remaining: " & RoundUp(10-Countdown.Value/1000, 0)**

    想要了解有关 **[RoundUp](../functions/function-round.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

    标签显示还有多少秒计时器重启。

### <a name="animate-a-control"></a>为控件添加动画效果
1. 添加一个计时器，并将其命名为 **FadeIn**。

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 将计时器的 **“Duration”** 属性设置为 **“5000”** ，将其 **“Repeat”** 属性设置为 **“true”** ，并将其 **[“Text”](properties-core.md)** 属性设置为“切换动画”。
3. （可选）通过以下方法可使计时器更易于读取：将其 **[Height](properties-size-location.md)** 属性设置为 **160**， **[Width](properties-size-location.md)** 属性设置为 **600**，并将其 **[Size](properties-text.md)** 属性设置为 **60**。
4. 添加一个标签，然后将“[Text](properties-core.md)”属性设置为显示“Welcome!” 并将其 **[Color](properties-color-border.md)** 属性设置为以下公式：
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    想要了解有关 **[ColorFade](../functions/function-colors.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

5. 选择计时器按钮以启动或停止动画。 标签中的文本渐变为白色，恢复最大亮度，并重复此过程。

## <a name="accessibility-guidelines"></a>辅助功能准则
如果用户可以与 " **Timer** " 控件交互，则该 **[按钮](control-button.md)** 控件的准则同样适用于该控件。

### <a name="background-timers"></a>背景计时器
后台计时器会自动运行并处于隐藏状态。 在支持角色中使用这些资源，该角色中的时间对用户不感兴趣。 例如，你可以每分钟刷新一次数据，或仅在特定的一段时间内显示一条通知消息。

背景计时器应将 **[Visible](properties-core.md)** 属性设置为 false，以便对所有用户隐藏它们。

### <a name="timing-considerations"></a>计时注意事项
如果**计时器**自动运行，请考虑用户是否有足够的时间来读取和使用内容。 键盘和屏幕阅读器用户可能需要更多的时间来响应定时事件。

这些策略中的任何一种都足以：
* 允许用户取消定时事件。
* 允许用户在开始之前调整时间限制。
* 在时间限制到期之前警告20秒，并提供一种简单的方法来扩展限制。

某些情况不受这些要求的限制。 请参阅[有关时间限制的 WCAG 2.0 准则](https://www.w3.org/TR/WCAG20/#time-limits)了解详细信息。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 如果计时器在当前屏幕上触发更改，请使用[实时区域](../accessible-apps-live-regions.md)告诉屏幕阅读器用户发生了哪些更改。

    > [!NOTE]
    > 如果计时器可见并正在运行，屏幕阅读器将每五秒公布经过的时间。

* 不要使用控件的 " **[Text](properties-core.md)** " 属性来区分时间信息和重要信息。 屏幕阅读器不会公告对 **[文本](properties-core.md)** 所做的更改。
* 对于交互式计时器：
    * **[“Text”](properties-core.md)** 必须存在。
    * 请考虑添加 " **[标签](control-text-box.md)** " 控件以显示运行时间。 使用计时器的 **[Text](properties-core.md)** 属性指示用户启动或停止计时器。
