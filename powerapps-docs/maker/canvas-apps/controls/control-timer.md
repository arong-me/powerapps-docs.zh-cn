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
ms.openlocfilehash: 5d20e2324f2efb4f866ed4fc183f289733c10a41
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560458"
---
# <a name="timer-control-in-powerapps"></a>PowerApps 中的计时器控件
一个控件，可确定特定时间后应用的响应方式。

## <a name="description"></a>描述
例如，计时器可确定控件显示的时长，或在经过特定时间后更改控件的其他属性。

> [!NOTE]
> 在 PowerApps Studio 计时器只在预览模式下运行。


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

**[FontWeight](properties-text.md) ** – 控件中文本的粗细：**加粗**，**半粗体**，**正常**，或**较浅**。

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
相同准则 **[按钮](control-button.md)** 控制将应用于**计时器**控制如果用户可以与其进行交互。

### <a name="background-timers"></a>后台计时器
后台计时器自动运行并处于隐藏状态。 使用它们支持角色中的已用时间都太感兴趣的用户。 例如，可以刷新每隔一分钟的数据，或仅对一定的时间显示一条通知消息。

后台计时器应具有其 **[Visible](properties-core.md)** 属性设置为 false，以便它们隐藏的所有用户。

### <a name="timing-considerations"></a>计时注意事项
如果**计时器**运行自动，考虑用户是否具有足够的时间来阅读和使用内容。 键盘和屏幕阅读器用户可能需要更多时间来响应定时事件。

任何这些策略均足以：
* 允许用户取消定时的事件。
* 允许用户在开始之前调整时间限制。
* 时间限制到期前的 20 秒，则发出警告，并提供轻松扩展限制。

某些情况不受这些要求的限制。 请参阅[有关时间限制的 WCAG 2.0 准则](https://www.w3.org/TR/WCAG20/#time-limits)了解详细信息。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 如果计时器触发更改当前屏幕上的，使用[活动区域](../accessible-apps-live-regions.md)通知屏幕阅读器用户更改的内容。

    > [!NOTE]
    > 如果计时器处于可见且正在运行，屏幕阅读器将公布经过的时间每隔 5 秒。

* 不要使用 **[文本](properties-core.md)** 时间敏感型和重要信息的控件属性。 屏幕读取器不会公布变为 **[文本](properties-core.md)** 。
* 有关交互式计时器：
    * **[“Text”](properties-core.md)** 必须存在。
    * 请考虑添加 **[标签](control-text-box.md)** 控件以显示所经过的时间。 使用计时器 **[文本](properties-core.md)** 属性以指示用户启动或停止计时器。
