---
title: "按钮控件：参考 | Microsoft 文档"
description: "了解按钮控件（包括属性和示例）"
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
ms.openlocfilehash: dfb50597af4012fe6145664fb645439a54686825
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="button-control-in-powerapps"></a>PowerApps 中的按钮控件
用户单击或点击后可与应用进行交互的控件。

## <a name="description"></a>说明
将“按钮”控件的**[“OnSelect”](properties-core.md)**属性配置为，在用户单击或点击控件时运行一个或多个公式。

## <a name="key-properties"></a>关键属性
**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**AutoDisableOnSelect** - 在“OnSelect”行为运行时自动禁用控件。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** - 控件具有键盘焦点时的边框粗细。

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

**[PaddingBottom](properties-size-location.md)** - 控件中的文本与此控件的下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** – 控件中的文本与该控件上边缘之间的距离。

Pressed - 如果用户按下控件，值为“true”，否则值为“false”。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[RadiusBottomLeft](properties-size-location.md)** – 控件左下角圆角的程度。

**[RadiusBottomRight](properties-size-location.md)** – 控件右下角圆角的程度。

**[RadiusTopLeft](properties-size-location.md)** – 控件左上角圆角的程度。

**[RadiusTopRight](properties-size-location.md)** – 控件右上角圆角的程度。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[VerticalAlign](properties-text.md)** – 控件上的文本相对于该控件垂直居中的位置。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
**[Navigate( ScreenName, ScreenTransitionValue )](../functions/function-navigate.md)**

## <a name="examples"></a>示例
### <a name="add-a-basic-formula-to-a-button"></a>向按钮添加基本公式
1. 添加**[“文本输入”](control-text-input.md)**控件，然后将其命名为“Source”。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加“按钮”控件，将“[Text](properties-core.md)”属性设置为“Add”，并将“[OnSelect](properties-core.md)”属性设置为以下公式：<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    想要详细了解 **[UpdateContext](../functions/function-updatecontext.md)** 函数或[其他函数](../formula-reference.md)吗？
3. 添加“[标签](control-text-box.md)”控件，将“[Text](properties-core.md)”属性设置为“Total”，再按 F5 键。
4. 清除“源”中的默认文本，键入数字，再单击或点击“添加”。
   
    此时，“[标签](control-text-box.md)”控件显示所键入的数字。
5. 清除“源”中的数字，键入另一个数字，再单击或点击“添加”。
   
    此时，“[标签](control-text-box.md)”控件显示键入的两个数字之和。
6. （可选）重复执行上述步骤一次或多次。
7. 若要返回到默认工作区，请按 Esc 键（或单击或点击右上角的关闭图标）。

### <a name="configure-a-button-with-multiple-formulas"></a>使用多个公式配置按钮
添加用于在两次输入间隔清除“文本输入”控件的公式。

1. 将“源”的“[HintText](control-text-input.md)”属性设置为“输入一个数字”。
2. 将“添加”的“[OnSelect](properties-core.md)”属性设置为以下公式：
   
    **UpdateContext({Total:Total + Value(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
> 请用分号“;”隔开多个公式。
3. 将“源”的“[Default](properties-core.md)”属性设置为“ClearInput”。
4. 按 F5，再通过同时添加多个数字来测试应用。

### <a name="add-another-button-to-reset-the-total"></a>添加另一个总和重置按钮
添加另一个按钮，以便在两次计算间隔清除总和。

1. 添加另一个“按钮”控件，将“[Text](properties-core.md)”属性设置为“Clear”，并将“[OnSelect](properties-core.md)”属性设置为以下公式：
   
    **UpdateContext({Total:0})**
2. 按 F5，将多个数字相加，再单击或点击“清除”来重置总和。

### <a name="change-a-buttons-appearance"></a>更改按钮外观
#### <a name="change-a-buttons-shape"></a>更改按钮形状
默认情况下，PowerApps 创建具有圆角的矩形“按钮”控件。 可以设置“[Height](properties-size-location.md)”、“[Width](properties-size-location.md)”和“[Radius](properties-size-location.md)”属性，对“按钮”控件的形状进行基本修改。

> [!NOTE]
> [“图标”和“形状”](control-shapes-icons.md)提供了各种设计，并可执行“按钮”控件执行的一些基本函数。 不过，“[图标和形状](control-shapes-icons.md)”没有“[Text](properties-core.md)”属性。

1. 添加“按钮”控件，并将“[Height](properties-size-location.md)”和“[Width](properties-size-location.md)”属性设置为“300”，以生成大方形按钮。
2. 修改“[RadiusTopLeft](properties-size-location.md)”、“[RadiusTopRight](properties-size-location.md)”、“[RadiusBottomLeft](properties-size-location.md)”，和“[RadiusBottomRight](properties-size-location.md)”属性，以调整每个角的曲率。 下面的示例展示了一些不同形状的按钮，每种都在 300x300 方形按钮基础之上生成：
   
   * 将所有四个“[Radius](properties-size-location.md)”值设置为“150”，以创建圆形按钮。
   * 将“[RadiusTopLeft](properties-size-location.md)”和“[RadiusBottomRight](properties-size-location.md)”的值设置为“300”，以创建叶形“按钮”控件。
   * 将“[RadiusTopLeft](properties-size-location.md)”和“[RadiusTopRight](properties-size-location.md)”的值设置为“300”，并将“[RadiusBottomLeft](properties-size-location.md)”和“[RadiusBottomRight](properties-size-location.md)”的值设置为“100”，以创建选项卡形状的按钮。

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>更改按钮的鼠标悬停颜色
默认情况下，当有鼠标悬停在“按钮”控件之上时，填充颜色会变暗 20%。 可以通过更改使用“[ColorFade](../functions/function-colors.md)”函数的“[HoverFill](properties-color-border.md)”属性来调整此行为。 如果将“[ColorFade](../functions/function-colors.md)”公式设置为正百分比，当有鼠标悬停在按钮之上时，颜色会变浅；而如果将此公式设置为负百分比，则鼠标悬停颜色将会变深。

* 更改所创建的一个按钮的“[HoverFill](properties-color-border.md)”属性中的“[ColorFade](../functions/function-colors.md)”百分比，并观察效果。

也可以将按钮的“[HoverFill](properties-color-border.md)”属性设置为包含“[ColorValue](../functions/function-colors.md)”函数（而不是“[ColorFade](../functions/function-colors.md)”函数）的公式，从而指定“按钮”的颜色，如 ColorValue("Red") 所示。

> [!NOTE]
> 颜色值可以是任意 CSS 颜色定义（可以是名称，也可以是十六进制值）。

* 在创建的一个按钮中，将“[ColorFade](../functions/function-colors.md)”函数替换为“[ColorValue](../functions/function-colors.md)”函数，并观察效果。

