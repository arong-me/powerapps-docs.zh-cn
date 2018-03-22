---
title: 添加图片控件：参考 | Microsoft 文档
description: 有关添加图片控件的信息（包括属性和示例）
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
ms.openlocfilehash: 6a7c60755f5623803d20bec4ec9881108b1116c6
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="add-picture-control-in-powerapps"></a>PowerApps 中的添加图片控件
拍摄照片或加载本地设备中的图像。

## <a name="description"></a>说明
借助此控件，用户可以拍摄照片或者上传自己设备中的图像文件，并使用此内容更新数据源。 在移动设备上，用户将看到设备的选择对话框，以供在拍摄照片或选择已有照片之间进行选择。

此控件是一个复合控件，由两个控件组成。  按下或点击即可选择外部控件（显示已上传的图像）。  再次按下或点击即可选择内部标签控件。

## <a name="outer-control-properties"></a>外部控件属性
这些属性应用于外部控件。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**Error** - 如果在上传图像时出现问题，该属性将包含相应的错误字符串。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**Media** - 音频或视频控件播放的剪辑的标识符。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

[Y](properties-size-location.md) - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="inner-text-properties"></a>内部文本属性
这些属性适用于默认显示“单击或点击以添加图片”的内部标签控件。  要选择此内部控件，请按下或点击“添加图片”控件一次，然后再重复一次。

**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[Padding](properties-size-location.md)** – 导入或导出按钮上的文本和该按钮边缘之间的距离。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[VerticalAlign](properties-text.md)** – 控件上的文本相对于该控件垂直居中的位置。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例
### <a name="add-images-to-an-image-gallery-control"></a>向图像库控件添加图像
1. 添加“添加图片”控件，然后三击该控件。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 在“打开”对话框中，单击或点击图像文件，然后单击或点击“打开”。
3. 添加“[按钮](control-button.md)”控件，将其移到“添加图片”控件下方，然后将“[按钮](control-button.md)”控件的 “[OnSelect](properties-core.md)”属性设置为以下公式：<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
4. 添加“图像库”控件，并将其 “[项](properties-core.md)” 属性设置为 **MyPix**。
5. 按 F5，然后单击或点击“[按钮](control-button.md)”控件。
   
    来自“添加图片”控件的图像将显示在“图像库”控件中。 如果图像和“图像库”控件中的“[图像](control-image.md)”控件纵横比不相同，请将“[图像](properties-visual.md)”[”控件的“](control-image.md)ImagePosition 属性设置为“适应”。
6. 单击或点击“添加图片”控件，单击或点击另一个图像文件，单击或点击“打开”，然后单击或点击所添加的“[按钮](control-button.md)”控件。
   
    第二个图像将显示在“图像库”控件中。
7. （可选）重复上述步骤一次或多次，然后按 Ecs 返回默认工作区。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数本地保存图像或使用 **[Patch](../functions/function-patch.md)** 函数更新数据源。

