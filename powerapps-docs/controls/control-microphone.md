---
title: "麦克风控件：参考 | Microsoft 文档"
description: "有关麦克风控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 3ffede0018a371b3c3a4cf4a3a1f9fc8115140de
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="microphone-control-in-powerapps"></a>PowerApps 中的麦克风控件
用户可以用来记录声音的控件。

## <a name="description"></a>说明
如果添加此控件，用户可从应用运行的任何位置使用一个或多个声音更新数据源。

## <a name="key-properties"></a>关键属性
**Mic** – 在具有多个麦克风的设备上，应用所使用的麦克风的数字 ID。

**OnStop** – 用户使用麦克风控件停止录制时应用的响应方式。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Image](properties-visual.md)** – 在图像、音频或麦克风控件中显示的图像名称。

**[ImagePosition](properties-visual.md)** – 屏幕或控件与图像大小不同时图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnStart** – 用户使用麦克风控件开始录制时应用的响应方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Reset](properties-core.md)** – 控件是否还原为其默认值。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例
### <a name="add-sounds-to-a-custom-gallery-control"></a>将声音添加到自定义库控件
1. 添加“麦克风”，将其命名为“MyMic”，并将其 **OnStop** 属性设置为以下公式：<br>
   **Collect(MySounds, MyMic.Audio)**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 添加“自定义库”控件，将其移至“MyMic” 下，并将“自定义库”控件的 **[Items](properties-core.md)** 属性设置为 **Mysounds**。
3. 在“自定义库”控件的模板中，添加**[音频](control-audio-video.md)**控件，并将其“媒体”属性设置为 **ThisItem.Url**。
4. 按 F5，单击或点击“MyMic”开始录制，然后再次单击或点击以停止录制。
5. 在“自定义库”控件中，单击或点击**[音频](control-audio-video.md)**控件中的播放按钮以播放录制的内容。
6. 根据需要添加多个录制内容，然后按 Esc 返回到默认工作区。
7. （可选）在“自定义库”控件的模板中，添加**[按钮](control-button.md)**控件，将 其 **[OnSelect](properties-core.md)** 属性设置为 **Remove(MySounds, ThisItem)**，按 F5，然后单击或点击相应的“按钮”控件删除录制。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数在本地保存录音，或使用 **[Patch](../functions/function-patch.md)** 函数更新数据源。

