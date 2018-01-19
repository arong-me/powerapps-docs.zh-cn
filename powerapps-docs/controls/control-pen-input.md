---
title: "笔输入控件：参考 | Microsoft 文档"
description: "有关笔输入控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 7e5be9b68b501279329c23f9afe5d451487fa8d1
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="pen-input-control-in-powerapps"></a>PowerApps 中的笔输入控件
用户可用其进行绘图、擦除和突出显示图像区域的控件。

## <a name="description"></a>说明
用户可以像使用白板一样来使用该控件，绘制关系图和写字都能被转换为键入的文本。

## <a name="key-properties"></a>关键属性
**[Color](properties-color-border.md)** – 输入笔划的颜色。

**Mode**控件所处的**绘图**或**擦除**模式。  已弃用“选择”模式。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**Input** - 输入。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[SelectionColor](properties-color-border.md)** - 所选项目或列表中项目的文本颜色，或笔控件中所选工具的颜色。

**SelectionThickness** - 笔输入控件的选择工具的粗细。

**ShowControls** – 音频或视频播放器是否显示播放按钮和音量滑块等组件，笔控件是否显示绘图、擦除和清除图标等。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Collect**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>示例
### <a name="create-a-set-of-images"></a>创建一组图像
1. 添加**笔输入**控件，将其命名为 **MyDoodles**，然后将其 **ShowControls** 属性设置为 **true**。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加[按钮](control-button.md)控件，将其移到 **MyDoodles** 下方，然后设置[按钮](control-button.md)控件的 [Text](properties-core.md) 属性，使其显示为“添加”。
3. 将此**[按钮](control-button.md)**控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **收集 (Doodles，{草： MyDoodles.Image})**
4. 添加**图像库**控件，将其移到[按钮](control-button.md)控件下方，然后缩小**图像库**控件的宽度，直至它显示三个项。
5. 将**映像库**控件的[项](properties-core.md)属性设置为 **Doodles**，然后再按 F5。
6. 在 **MyDoodles** 中绘制图像，然后单击或点击[按钮](control-button.md)控件。
   
    绘制的图像将在“图像库”控件中显示。
7. （可选）在“笔输入”控件中，单击或点击图标，清除所绘制的图像，绘制另一个图像，再单击或点击[按钮](control-button.md)控件。
8. 在**图像库**控件中，将**[图像](control-image.md)**控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **删除 (Doodles，ThisItem)**
9. 单击或点击“图像库”控件中的绘图，可将其删除。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数本地保存绘图，或使用 **[Patch](../functions/function-patch.md)** 函数将其保存至数据源。

