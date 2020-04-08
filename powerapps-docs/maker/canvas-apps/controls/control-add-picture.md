---
title: 添加图片控件：参考 | Microsoft 文档
description: 有关添加图片控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3f2afd3a1097ec0b201b5857509f1ff42d1fedad
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871272"
---
# <a name="add-picture-control-in-power-apps"></a>在 Power Apps 中添加图片控件
拍摄照片或加载本地设备中的图像。

## <a name="description"></a>说明
借助此控件，用户可以拍摄照片或者上传自己设备中的图像文件，并使用此内容更新数据源。 在移动设备上，用户将看到设备的选择对话框，以供在拍摄照片或选择已有照片之间进行选择。

此控件是包含两个控件的分组控件：**图像**和 "**添加图片" 按钮**。 如果不上传任何图像，“图像”控件将显示已上传的图像或占位符。 "**添加图片" 按钮**提示输入要上传的图像。

有关“图像”属性，请参阅[图像控件引用](control-image.md)。

## <a name="add-picture-button-properties"></a>添加图片按钮属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应描述添加图片的用途。

**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

ChangePictureText – 上传图像时按钮上显示的文本。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[DisabledColor](properties-color-border.md)** – 控件的 **[DisplayMode](properties-core.md)** 属性设置为 Disabled**Disabled** 时，该控件中的文本颜色。

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode” **[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**Error** - 如果在上传图像时出现问题，该属性将包含相应的错误字符串。

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

**Media** – 音频或视频控件播放的剪辑的标识符。

[OnChange](properties-core.md) – 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[Padding](properties-size-location.md)** – 导入或导出按钮上的文本和该按钮边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

[Reset](properties-core.md) – 是否还原控件的默认值。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

[Strikethrough](properties-text.md) – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

[Text](properties-core.md) – 未上传图像时按钮上显示的文本。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

[VerticalAlign](properties-text.md) – 控件上的文本相对于该控件垂直居中的位置。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="examples"></a>示例
### <a name="add-images-to-an-image-gallery-control"></a>向图像库控件添加图像
1. 添加“添加图片”控件，然后三击该控件。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
1. 在“打开”对话框中，单击或点击图像文件，然后单击或点击“打开”。
1. 添加“[按钮](control-button.md)”控件，将其移到“添加图片”控件下方，然后将“[按钮](control-button.md)”控件的 “[OnSelect](properties-core.md)”属性设置为以下公式：<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
1. 添加**垂直库**控件，并将其 **[Items](properties-core.md)** 属性设置为**MyPix**。
1. 选择库中的 " **[图像](control-image.md)** " 控件，并将其 " **image** " 属性设置为 " **ThisItem**"。
1. 按 F5，然后单击或点击“[按钮](control-button.md)”控件。
   
    "**添加图片**" 控件中的图像将显示在**垂直 allery**控件中。 如果图像与 "**垂直库**" 控件中的 **[图像](control-image.md)** 控件具有相同的纵横比，请将 **[图像](control-image.md)** 控件的 " **[ImagePosition](properties-visual.md)** " 属性设置为 "**适合**"。
1. 单击或点击“添加图片”控件，单击或点击另一个图像文件，单击或点击“打开”，然后单击或点击所添加的“[按钮](control-button.md)”控件。
   
    第二个图像将显示在“图像库”控件中。
1. （可选）重复上述步骤一次或多次，然后按 Ecs 返回默认工作区。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数本地保存图像或使用 **[Patch](../functions/function-patch.md)** 函数更新数据源。


## <a name="accessibility-guidelines"></a>辅助功能准则
适用[按钮](control-button.md)和[图像](control-image.md)的相同准则。 此外，请考虑以下方面：

### <a name="color-contrast"></a>颜色对比度
* "**添加图片" 按钮**的文本和背景必须具有足够的对比度。 由于上传的图像可能具有不同的颜色，因此请在 "**添加图片" 按钮**上使用不透明 **[填充](properties-color-border.md)** 以确保对比度一致。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* "**添加图片" 按钮**的**文本**和**ChangePictureText**必须提示用户添加或更改图片。

### <a name="keyboard-support"></a>键盘支持
* "**添加图片" 按钮**的 **[TabIndex](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* "**添加图片" 按钮**必须具有明显可见的聚焦标记。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
 
