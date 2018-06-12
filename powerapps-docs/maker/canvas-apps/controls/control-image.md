---
title: 图像控件：参考 | Microsoft Docs
description: 有关图像控件的信息（包括属性和示例）
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: bd07c6ee0a0084171c928c6908c33caae974d765
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31835131"
---
# <a name="image-control-in-powerapps"></a>PowerApps 中的图像控件
显示来自本地文件或数据源等来源的图像的控件。

## <a name="description"></a>说明
如果向应用添加了一个或多个“图像”控件，则可以显示不属于数据集的单个图像，也可以合并数据源中的记录的图像。

## <a name="key-properties"></a>关键属性
[Image](properties-visual.md) – 在图像、音频或麦克风控件中显示的图像名称。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**ApplyEXIFOrientation** – 是否自动应用随图像一起嵌入的 EXIF 数据中指定的方向。

**AutoDisableOnSelect** – 在执行 OnSelect 行为时自动禁用控件。

[BorderColor](properties-color-border.md) – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

[BorderThickness](properties-color-border.md) – 控件边框的粗细。

CalculateOriginalDimensions – 启用“OriginalHeight”和“OriginalWidth”属性。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件的背景色。

[Fill](properties-color-border.md) – 控件的背景色。

FlipHorizontal – 是否在显示前先水平翻转图像。

FlipVertical – 是否在显示前先垂直翻转图像。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverFill](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件的背景色。

[ImagePosition](properties-visual.md) – 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

ImageRotation – 如何在显示前旋转图像。  值可以是不旋转、顺时针 (CW) 旋转 90 度、逆时针 (CCW) 旋转 90 度和顺时针旋转 180 度。

[OnSelect](properties-core.md) – 用户点击或单击某个控件时应用响应的方式。

OriginalHeight – 使用“CalculateOriginalDimensions”属性启用的图像的原始高度。

OriginalWidth – 使用“CalculateOriginalDimensions”属性启用的图像的原始宽度。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

[PaddingTop](properties-size-location.md) – 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[RadiusBottomLeft](properties-size-location.md)** – 控件左下角圆角的程度。

**[RadiusBottomRight](properties-size-location.md)** – 控件右下角圆角的程度。

**[RadiusTopLeft](properties-size-location.md)** – 控件左上角圆角的程度。

[RadiusTopRight](properties-size-location.md) – 控件右上角圆角的程度。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

Transparency – 图像后的控件仍然可见的程度。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[Remove( DataSource, ThisItem )](../functions/function-remove-removeif.md)

## <a name="examples"></a>示例
### <a name="show-an-image-from-a-local-file"></a>显示来自本地文件的图像
1. 在“文件”菜单上，依次单击或点击“媒体”和“浏览”。
2. 单击或点击要添加的图像文件，然后单击或点击“打开”，按 Esc 返回到默认工作区。
3. 添加“图像”控件，并将它的“Image”属性设置为添加的文件的名称。

    不知道如何[添加和配置控件](../add-configure-controls.md)？

    “图像”控件显示你指定的图像。

### <a name="show-a-set-of-images-from-a-data-source"></a>显示一组数据源的图像
1. 下载此 [Excel 文件](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)，并将其保存在本地设备上。
2. 在 PowerApps Studio 中，创建或打开应用，再单击或点击右侧窗格中的“添加数据源”。

    如果右侧窗格未显示“添加数据源”选项卡，请单击或点击左侧导航栏中的任意屏幕。
3. 单击或点击“将静态数据添加到应用”，单击或点击已下载的 Excel 文件，然后单击或点击“打开”。
4. 选择“地板估计”复选框，然后单击或点击“连接”。
5. 添加带图像的“库”控件，并将 [Items](properties-core.md) 属性设置为“FlooringEstimates”。

    不知道如何[添加和配置控件](../add-configure-controls.md)？

    “库”控件根据所下载的 Excel 文件中的链接显示地毯、硬木和地砖产品的图像。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
* 如果图形用作按钮，则[标准颜色对比度要求](../accessible-apps-color.md)适用。
* 如果它不仅仅用于修饰，则考虑检查图像中的对比度问题。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 如果图形用作按钮或者不仅仅用于修饰，则**[“AccessibleLabel”](properties-accessibility.md)** 必须存在。
* 如果图形纯粹用于修饰作用，**[“AccessibleLabel”](properties-accessibility.md)** 必须为空或空字符串 ""。 这将导致屏幕阅读器忽略图形。
* 如果图形提供冗余信息，**[“AccessibleLabel”](properties-accessibility.md)** 可以为空或空字符串 ""。
    * 例如，齿轮的“图像”将其**[“AccessibleLabel”](properties-accessibility.md)** 设置为“Settings”。 此图像不用作按钮。 它位于同样显示“Settings”的**[标签](control-text-box.md)** 旁边。 屏幕阅读器将图像读作“Settings”，并再次将标签读作“Settings”。 没必要对此进行详细说明。 在此情况下，该图像不需要**[“AccessibleLabel”](properties-accessibility.md)**。

    > [!IMPORTANT]
> 屏幕阅读器将始终读取 **[TabIndex](properties-accessibility.md)** 为零或更大的图像，即使**[“AccessibleLabel”](properties-accessibility.md)** 为空。 这是因为它们以按钮形式呈现。 如果没有提供**[“AccessibleLabel”](properties-accessibility.md)**，屏幕阅读器只需将图形读作“按钮”。

### <a name="keyboard-support"></a>键盘支持
* 如果图形用作按钮，**[“TabIndex”](properties-accessibility.md)** 必须为零或更大。 这允许键盘用户导航到它。
* 如果图形用作按钮，焦点指示器必须清楚显示。 可以使用**[“FocusedBorderColor”](properties-color-border.md)** 和**[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。

    > [!NOTE]
> 当**[“TabIndex”](properties-accessibility.md)** 为零或更大，图像将以按钮形式呈现。 可视外观没有变化，但屏幕阅读器将正确识别作为按钮的图像。 当**[“TabIndex”](properties-accessibility.md)** 小于零，图像将被标识为图像。
