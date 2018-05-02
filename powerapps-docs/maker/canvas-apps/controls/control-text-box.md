---
title: 标签控件：参考 | Microsoft 文档
description: 介绍了标签控件，包括属性和示例
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
ms.openlocfilehash: e3cae08695af7a4625fd4deb58c8cf7cfe71fdd0
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="label-control-in-powerapps"></a>PowerApps 中的标签控件
一个框，显示文本、数字、日期或货币等数据。

## <a name="description"></a>描述
标签按键入时原封不动地显示指定为文本字符串的数据，或显示指定为公式（计算结果为文本字符串）的数据。 标签通常作为标识另一控件（如评分或音频控件）的标签出现在其他任何控件（如标识屏幕的横幅）之外，或出现在库中以显示项的特定类型信息。

## <a name="key-properties"></a>关键属性
**[AutoHeight](properties-core.md)** - 设置为 true 后，标签会自动调高高度，以显示配置的所有文本。 设置为“false”将文本截断至分配的高度。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

**[DelayOutput](properties-core.md)** - 设置为 true，可在文本输入期间延迟操作。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**AutoHeight** - 标签是否会在“[Text](properties-core.md)”属性包含的字符数超过控件一次可显示的字符数时自动增加“[Height](properties-size-location.md)”属性值。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的“DisplayMode”**[](properties-core.md)** 属性设置为“Disabled”时，该控件的背景色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[LineHeight](properties-text.md)** - 诸如文本行之间或列表中各项之间的距离。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

Overflow – 标签是否会在“Wrap”属性设置为“true”且“[Text](properties-core.md)”属性值包含的字符数超过控件一次可显示的字符数时显示滚动条。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[VerticalAlign](properties-text.md)** – 控件上的文本相对于该控件垂直居中的位置。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**Wrap** - 太长而无法容纳在标签中的文本是否换到下一行。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Text**( *Number*, "*FormatCodes*" )](../functions/function-text.md)

## <a name="examples"></a>示例
### <a name="show-a-literal-string"></a>显示文本字符串
* 添加一个标签，然后将“[Text](properties-core.md)”属性设置为“"Hello, world"”（含双引号）。
  
    不知道如何[添加和配置控件](../add-configure-controls.md)？

### <a name="show-the-result-of-a-formula"></a>显示公式的结果
* 添加一个标签，然后将“[Text](properties-core.md)”属性设置为如下公式：<br>
  **Today()**
  
    > [!NOTE]
> 指定公式时，请勿使用引号，除非公式的参数是文本字符串。 在这种情况下，用双引号将参数（而不是公式）括住。
  
    想要了解有关 **[Today](../functions/function-now-today-istoday.md)** 函数或[其他函数](../formula-reference.md)的详细信息？

### <a name="show-data-in-a-gallery"></a>在库中显示数据
在此过程中，需创建一个名为 **CityPopulations** 的集合，其中包含欧洲各个城市人口的相关数据。 接下来，在包含三个标签的库中显示数据，然后指定每个标签将显示的数据类型。

1. 添加一个按钮，然后将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. 按 F5，选择该按钮，然后按 Esc。
3. 添加一个文本库，然后将其 **[Items](properties-core.md)** 属性设置为 **CityPopulations**。
   
    选择库后，右侧窗格显示该库的选项。
4. 在“Gallery1”窗格中，将顶部列表设置为“Population”，中间列表设置为“City”，底部列表设置为“Country”。


## <a name="accessibility-guidelines"></a>辅助功能准则
尽管其名称如此，“标签”控件不一定要用作另一个控件的标签。 它可以用于显示文本的任何部分。

可以通过指定 OnSelect**[](properties-core.md)** 行为，将“标签”作为按钮或链接使用。 以此方式使用时，要考虑与按钮相类似的辅助功能注意事项。

### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* Color**[](properties-color-border.md)** 和 Fill**[](properties-color-border.md)**
* 其他标准颜色对比度要求适用（如果用作按钮或链接）

### <a name="screen-reader-support"></a>屏幕阅读器支持
* “Text”**[](properties-core.md)** 必须存在。
> [!NOTE]
> 当“TabIndex”**[](properties-accessibility.md)** 为零或更大，屏幕阅读器会将“标签”视为按钮。

### <a name="low-vision-support"></a>弱视支持
* 如果“标签”作为链接使用，则应采用链接的形式。
    * 将“Underline”**[](properties-text.md)** 设置为 true
    * “HoverColor”**[](properties-color-border.md)** 应不同于“Color”**[](properties-color-border.md)**

### <a name="keyboard-support"></a>键盘支持
* 如果文本用作按钮或链接，“TabIndex”**[](properties-accessibility.md)** 必须为零或更大。 这允许键盘用户导航到它。
* 如果文本用作按钮或链接，焦点指示器必须清楚显示。 可以使用“FocusedBorderColor”**[](properties-color-border.md)** 和“FocusedBorderThickness**[](properties-color-border.md)**”来实现此目的。
