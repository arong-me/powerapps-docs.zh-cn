---
title: 笔输入控件：参考 | Microsoft 文档
description: 有关笔输入控件的信息（包括属性和示例）
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
ms.openlocfilehash: a5645f2f0d515d7eca125f3cd89ecff0c63cfa51
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729047"
---
# <a name="pen-input-control-in-power-apps"></a>Power Apps 中的笔输入控件
用户可用其进行绘图、擦除和突出显示图像区域的控件。

## <a name="description"></a>描述
用户可以像使用白板一样来使用该控件，绘制关系图和写字都能被转换为键入的文本。

## <a name="key-properties"></a>关键属性
图像 – 输出属性，表示由最终用户绘制的图像。

**[Color](properties-color-border.md)** – 输入笔划的颜色。

**Mode**控件所处的**绘图**或**擦除**模式。  已弃用“选择”模式。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 可以用于描述控件的用途以及输入的替代方法。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

输入 – 已弃用。 输入是否支持鼠标、触笔或触控输入。  默认值 (7) 支持上述所有三项。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[SelectionColor](properties-color-border.md)** - 所选项目或列表中项目的文本颜色，或笔控件中所选工具的颜色。

**SelectionThickness** - 笔输入控件的选择工具的粗细。

ShowControls – 音频或视频播放器是否显示播放按钮和音量滑块等组件，笔控件是否显示绘图、擦除和清除图标等。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Collect**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>示例
### <a name="create-a-set-of-images"></a>创建一组图像
1. 添加**笔输入**控件，将其命名为 **MyDoodles**，然后将其 **ShowControls** 属性设置为 **true**。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加[按钮](control-button.md)控件，将其移到 **MyDoodles** 下方，然后设置[按钮](control-button.md)控件的 [Text](properties-core.md) 属性，使其显示为“添加”。
3. 将此 **[按钮](control-button.md)** 控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. 添加**图像库**控件，将其移到[按钮](control-button.md)控件下方，然后缩小**图像库**控件的宽度，直至它显示三个项。
5. 将**映像库**控件的[项](properties-core.md)属性设置为 **Doodles**，然后再按 F5。
6. 在 **MyDoodles** 中绘制图像，然后单击或点击[按钮](control-button.md)控件。
   
    绘制的图像将在“图像库”控件中显示。
7. （可选）在“笔输入”控件中，单击或点击图标，清除所绘制的图像，绘制另一个图像，再单击或点击[按钮](control-button.md)控件。
8. 在 **图像库** 控件中，将 **[图像](control-image.md)** 控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Remove(Doodles, ThisItem)**
9. 单击或点击“图像库”控件中的绘图，可将其删除。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数本地保存绘图，或使用 **[Patch](../functions/function-patch.md)** 函数将其保存至数据源。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* **[BorderColor](properties-color-border.md)** 和控件范围之外的颜色（如果有边框）
* **[Fill](properties-color-border.md)** 和控件范围之外的颜色（如果没有边框）

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 应存在。

    > [!IMPORTANT]
  > 屏幕阅读器用户无法访问“笔输入”。 始终提供输入的替代形式。 例如，如果需要草图，请考虑添加 **[“添加图片”](control-add-picture.md)** 控件，以便用户上传图像。 可以提供这两种方法，用户可以选择他们更熟悉的一种方法。

### <a name="keyboard-support"></a>键盘支持

> [!IMPORTANT]
> 键盘用户无法访问“笔输入”。 始终提供输入的替代形式。 例如，如果需要签名，请考虑添加 **[“文本输入”](control-text-input.md)** ，以便用户输入其名称。 可以提供这两种方法，用户可以选择他们更熟悉的一种方法。
